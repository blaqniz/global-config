import javax.xml.namespace.QName;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.ws.WebServiceMessage;
import org.springframework.ws.client.core.support.WebServiceGatewaySupport;
import org.springframework.ws.soap.SoapHeaderElement;
import org.springframework.ws.soap.client.core.SoapActionCallback;
import org.springframework.ws.soap.saaj.SaajSoapMessage;
import javax.xml.bind.JAXBContext;
import javax.xml.bind.JAXBElement;
import javax.xml.bind.JAXBException;
import javax.xml.bind.Unmarshaller;

public class GenericSoapClient<T, R> extends WebServiceGatewaySupport {

    private static final Logger log = LoggerFactory.getLogger(GenericSoapClient.class);

    private final String action;
    private final String namespaceUri;
    private final String headerUri;
    private final Class<T> requestClass;
    private final Class<R> responseClass;
    private final Class<?> headerClass;

    public GenericSoapClient(String action, String namespaceUri, String headerUri, Class<T> requestClass, Class<R> responseClass, Class<?> headerClass) {
        this.action = action;
        this.namespaceUri = namespaceUri;
        this.headerUri = headerUri;
        this.requestClass = requestClass;
        this.responseClass = responseClass;
        this.headerClass = headerClass;
    }

    public R sendRequest(T request, SoapHeaderElement soapHeader) {
        log.info("Service call to SOAP client: " + this.getDefaultUri());

        JAXBElement<T> cleanRequest = new JAXBElement<>(new QName(namespaceUri, requestClass.getSimpleName()), requestClass, request);

        SoapActionCallback requestCallback = new SoapActionCallback(action) {
            public void doWithMessage(WebServiceMessage message) {
                try {
                    JAXBContext context = JAXBContext.newInstance(headerClass);
                    Unmarshaller unmarshaller = context.createUnmarshaller();
                    JAXBElement<?> ecHeader = (JAXBElement<?>) unmarshaller.unmarshal(soapHeader.getSource());

                    Object enterpriseContext = ecHeader.getValue();
                    SaajSoapMessage soapMessage = (SaajSoapMessage) message;

                    JAXBContext jaxbContext = JAXBContext.newInstance(headerClass);
                    JAXBElement<?> cleanEC = new JAXBElement<>(new QName(headerUri, enterpriseContext.getClass().getSimpleName()), (Class<Object>) enterpriseContext.getClass(), enterpriseContext);
                    jaxbContext.createMarshaller().marshal(cleanEC, soapMessage.getSoapHeader().getResult());

                } catch (JAXBException e) {
                    e.printStackTrace();
                }
            }
        };

        Object response = getWebServiceTemplate().marshalSendAndReceive(cleanRequest, requestCallback);
        return (R) ((JAXBElement<R>) response).getValue();
    }
}

You can instantiate and use the GenericSoapClient like this:

GenericSoapClient<RetrieveBusinessCaseDetailsRequestWrapperType, RetrieveBusinessCaseDetailsResponseWrapperType> client =
    new GenericSoapClient<>(
        "http://example.com/action",
        "http://example.com/namespace",
        "http://example.com/headerUri",
        RetrieveBusinessCaseDetailsRequestWrapperType.class,
        RetrieveBusinessCaseDetailsResponseWrapperType.class,
        EnterpriseContextType.class
    );

RetrieveBusinessCaseDetailsResponseWrapperType response = client.sendRequest(request, soapHeader);
