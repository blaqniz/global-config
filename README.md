# global-config
Global Property Configuration

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
import za.co.nednet.it.contracts.infrastructure._2008._09.enterprisecontext.EnterpriseContextType;
import za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.businesscaseinformation.v2.RetrieveBusinessCaseDetailsRequestWrapperType;
import za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.businesscaseinformation.v2.RetrieveBusinessCaseDetailsResponseWrapperType;

public class BusinessCaseManagementClient extends WebServiceGatewaySupport {

    private static final Logger log = LoggerFactory.getLogger(BusinessCaseManagementClient.class);

    private static final String ACTION = "http://contracts.it.nednet.co.za/service/biz/informationandtechnologymanagement/BusinessCaseInformation/v2/RetrieveBusinessCaseDetails";
    private static final String NAMESPACE_URI = "http://contracts.it.nednet.co.za/service/biz/informationandtechnologymanagement/BusinessCaseInformation/v2";
    private static final String HEADER_URI = "http://contracts.it.nednet.co.za/Infrastructure/2008/09/EnterpriseContext";

    public RetrieveBusinessCaseDetailsResponseWrapperType RetrieveBusinessCaseDetails(RetrieveBusinessCaseDetailsRequestWrapperType request, SoapHeaderElement soapHeader) {

        log.info("Service call to BusinessCaseManagement :" + this.getDefaultUri());

        JAXBElement<RetrieveBusinessCaseDetailsRequestWrapperType> cleanRQ = new JAXBElement<RetrieveBusinessCaseDetailsRequestWrapperType>(new QName(NAMESPACE_URI,
        "RetrieveBusinessCaseDetails"),
        RetrieveBusinessCaseDetailsRequestWrapperType.class, request);

        SoapActionCallback requestCallback = new SoapActionCallback(ACTION)
        {
            public void doWithMessage(WebServiceMessage message)
            {
                try {

                // create an unmarshaller
                JAXBContext context = JAXBContext.newInstance(za.co.nednet.it.contracts.infrastructure._2008._09.enterprisecontext.ObjectFactory.class);
                Unmarshaller unmarshaller;
                    unmarshaller = context.createUnmarshaller();


                @SuppressWarnings("unchecked")
                JAXBElement<EnterpriseContextType> ecHeader = (JAXBElement<EnterpriseContextType>) unmarshaller.unmarshal(soapHeader.getSource());

                    EnterpriseContextType enterpriseContext = ecHeader.getValue();

                //Create Response Body and Header
                SaajSoapMessage soapMessage = (SaajSoapMessage) message;

                //Send Response back (Classes marshalled)
                JAXBContext jaxbContext = JAXBContext.newInstance(EnterpriseContextType.class);
                JAXBElement<EnterpriseContextType> cleanEC = new JAXBElement<>(new QName(HEADER_URI, EnterpriseContextType.class.getSimpleName()),EnterpriseContextType.class, enterpriseContext);
                jaxbContext.createMarshaller().marshal(cleanEC, soapMessage.getSoapHeader().getResult());
                } catch (JAXBException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }

            }
        };


        //RetrieveBusinessCaseDetailsResponseWrapperType response = (RetrieveBusinessCaseDetailsResponseWrapperType) getWebServiceTemplate()
        //.marshalSendAndReceive(cleanRQ, requestCallback);

        Object response = getWebServiceTemplate().marshalSendAndReceive(cleanRQ, requestCallback);

        //return (RetrieveBusinessCaseDetailsResponseWrapperType) ((JAXBElement<RetrieveBusinessCaseDetailsResponseWrapperType>) response).getValue();
        return (RetrieveBusinessCaseDetailsResponseWrapperType) ((JAXBElement<RetrieveBusinessCaseDetailsResponseWrapperType>) response).getValue();
    }

}
