# global-config
Global Property Configuration


package com.fico.ps.nedbank.soap.client;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.oxm.jaxb.Jaxb2Marshaller;

@Configuration
public class ProductCatalogueClientConfig {

    private static final String CONTEXT_PATH = "za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.productcatalogue.v2";
    private final String defaultUri;

    public ProductCatalogueClientConfig(@Value("${service.product.catalogue.endpoint}") String defaultUri) {
        this.defaultUri = defaultUri;
    }

    @Bean
    public Jaxb2Marshaller marshaller() {
        Jaxb2Marshaller marshaller = new Jaxb2Marshaller();
//        marshaller.setContextPath("za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.productcatalogue.v2");
        return null;
    }

    @Bean
    public ProductCatalogueSoapClient client() {
        ProductCatalogueSoapClient client = new ProductCatalogueSoapClient();
        client.setDefaultUri("https://ssg-d.it.nednet.co.za:443/services/ent/productandservicedevelopment/channelproductcatalogue/v1");
        client.setMarshaller(marshaller());
        client.setUnmarshaller(marshaller());
        return client;
    }
}
