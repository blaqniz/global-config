# global-config
Global Property Configuration

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://maven.apache.org/POM/4.0.0"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.fico.ps.nedbank.epa</groupId>
    <artifactId>evaluatepartyapplication-ws</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>EvaluatePartyApplication</name>
    <description>Evaluate Party Application API</description>

    <packaging>war</packaging>

    <properties>
        <java.version>8</java.version>
        <blaze.version>7.8.0.0</blaze.version>
        <bom.version>1.0</bom.version>

        <spring.version>5.2.4.RELEASE</spring.version>
        <springintegration.version>5.1.5.RELEASE</springintegration.version>
        <springbatch.version>4.1.2.RELEASE</springbatch.version>
        <springws.version>3.0.7.RELEASE</springws.version>

    </properties>
    <dependencies>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-web</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-oxm</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-beans</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.ws</groupId>
            <artifactId>spring-ws-support</artifactId>
            <version>${springws.version}</version>
        </dependency>

        <dependency>
            <groupId>wsdl4j</groupId>
            <artifactId>wsdl4j</artifactId>
            <version>1.6.3</version>
        </dependency>

        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
            <version>1.2.3</version>
        </dependency>

        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-core</artifactId>
            <version>2.15.4</version>
        </dependency>

        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>2.15.4</version>
        </dependency>

        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-annotations</artifactId>
            <version>2.15.4</version>
        </dependency>

        <dependency>
            <groupId>com.fico.blaze</groupId>
            <artifactId>Advisor</artifactId>
            <version>${blaze.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>*</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.fico.blaze</groupId>
            <artifactId>AdvCommon</artifactId>
            <version>${blaze.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>*</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.fico.blaze</groupId>
            <artifactId>AdvisorSvr</artifactId>
            <version>${blaze.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>*</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.fico.blaze</groupId>
            <artifactId>InnovatorRT</artifactId>
            <version>${blaze.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>*</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.fico.ps.nedbank.brm.evaluatepartyapplication</groupId>
            <artifactId>evaluatepartyapplication-bom</artifactId>
            <version>${bom.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>com.fico.blaze</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.ibm.websphere.appserver.api</groupId>
            <artifactId>com.ibm.websphere.appserver.api.ssl</artifactId>
            <version>1.5.66</version>
        </dependency>
        <dependency>
            <groupId>com.github.danielwegener</groupId>
            <artifactId>logback-kafka-appender</artifactId>
            <version>0.2.0-RC2</version>
        </dependency>

        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-lang3</artifactId>
            <version>3.4</version>
        </dependency>

        <dependency>
            <groupId>org.json</groupId>
            <artifactId>json</artifactId>
            <version>20180813</version>
        </dependency>

        <dependency>
            <groupId>org.apache.ws.xmlschema</groupId>
            <artifactId>xmlschema-core</artifactId>
            <version>2.2.4</version>
        </dependency>

        <dependency>
            <groupId>javax.activation</groupId>
            <artifactId>activation</artifactId>
            <version>1.1.1</version>
        </dependency>

        <dependency>
            <groupId>javax.xml.soap</groupId>
            <artifactId>javax.xml.soap-api</artifactId>
            <version>1.4.0</version>
        </dependency>

        <dependency>
            <groupId>javax.xml.stream</groupId>
            <artifactId>stax-api</artifactId>
            <version>1.0-2</version>
        </dependency>

        <dependency>
            <groupId>javax.xml.ws</groupId>
            <artifactId>jaxws-api</artifactId>
            <version>2.3.1</version>
        </dependency>
        <dependency>
            <groupId>javax.jws</groupId>
            <artifactId>javax.jws-api</artifactId>
            <version>1.1</version>
        </dependency>

        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>4.0.1</version>
        </dependency>

        <dependency>
            <groupId>com.sun.xml.messaging.saaj</groupId>
            <artifactId>saaj-impl</artifactId>
            <version>1.5.1</version>
            <exclusions>
                <exclusion>
                    <groupId>junit</groupId>
                    <artifactId>junit</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.sun.xml.parsers</groupId>
            <artifactId>jaxp-ri</artifactId>
            <version>1.4.5</version>
        </dependency>

        <dependency>
            <groupId>com.sun.xml.bind</groupId>
            <artifactId>jaxb-core</artifactId>
            <version>2.3.0.1</version>
        </dependency>

        <dependency>
            <groupId>xalan</groupId>
            <artifactId>xalan</artifactId>
            <version>2.7.1</version>
            <exclusions>
                <exclusion>
                    <groupId>xml-apis</groupId>
                    <artifactId>xml-apis</artifactId>
                </exclusion>
                <exclusion>
                    <artifactId>xercesImpl</artifactId>
                    <groupId>xerces</groupId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/com.sun.xml.bind/jaxb-impl -->
        <dependency>
            <groupId>com.sun.xml.bind</groupId>
            <artifactId>jaxb-impl</artifactId>
            <version>2.0.1</version>
        </dependency>

    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.6.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>


            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>3.2.3</version>
                <configuration>
                    <warName>${project.artifactId}</warName>
                </configuration>
            </plugin>


            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>jaxb2-maven-plugin</artifactId>
                <version>2.5.0</version>
                <executions>
                    <execution>
                        <id>xjc</id>
                        <goals>
                            <goal>xjc</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <sources>
                        <source>src/main/resources/wsdl/business-case-information/EnterpriseContext_2008-09.xsd</source>
                        <source>
                            src/main/resources/wsdl/business-case-information/EvaluatePartyApplication_v1.0_Messages.xsd
                        </source>
                    </sources>
                    <outputDirectory>src/main/java</outputDirectory>
                    <clearOutputDir>false</clearOutputDir>
                </configuration>
            </plugin>

            <!-- tag::wsdl[] -->

            <plugin>
                <groupId>com.sun.xml.ws</groupId>
                <artifactId>jaxws-maven-plugin</artifactId>
                <version>2.3.2</version>
                <executions>
                    <!-- TODO: Replace this with CaseActivitiesManagement_v1.0_EC2SoapEndpoint.wsdl project
                            The CaseActivitiesManagement_v1.0_EC2SoapEndpoint.wsdl replaces OutstandingDocs & Business Case Manager
                    -->
                    <!--<execution>
                        <id>business-case-information</id>
                        <goals>
                            <goal>wsimport</goal>
                        </goals>
                        <configuration>
                            <packageName>
                                za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.businesscaseinformation.v2
                            </packageName>
                            <wsdlUrls>
                                <wsdlUrl>
                                    src/main/resources/wsdl/business-case-information/BusinessCaseInformation_v2.2_EC2SoapEndpoint.wsdl
                                </wsdlUrl>
                            </wsdlUrls>
                            <sourceDestDir>src/main/java</sourceDestDir>
                            <destDir>${classesDir}</destDir>
                            <extension>true</extension>
                        </configuration>
                    </execution>-->
                    <execution>
                        <id>case-cache</id>
                        <goals>
                            <goal>wsimport</goal>
                        </goals>
                        <configuration>
                            <packageName>
                                za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.casecache.v1
                            </packageName>
                            <wsdlUrls>
                                <wsdlUrl>
                                    src/main/resources/wsdl/case-cache/CaseActivitiesManagement_v1.0_EC2SoapEndpoint.wsdl
                                </wsdlUrl>
                            </wsdlUrls>
                            <sourceDestDir>src/main/java</sourceDestDir>
                            <destDir>${classesDir}</destDir>
                            <extension>true</extension>
                        </configuration>
                    </execution>
                    <execution>
                        <id>product-catalogue</id>
                        <goals>
                            <goal>wsimport</goal>
                        </goals>
                        <configuration>
                            <packageName>
                                za.co.nednet.it.contracts.service.biz.informationandtechnologymanagement.productcatalogue.v2
                            </packageName>
                            <wsdlUrls>
                                <wsdlUrl>
                                    src/main/resources/wsdl/product-catalogue/ChannelProductCatalogue_v2.0_EC2SoapEndpoint.wsdl
                                </wsdlUrl>
                            </wsdlUrls>
                            <sourceDestDir>src/main/java</sourceDestDir>
                            <destDir>${classesDir}</destDir>
                            <extension>true</extension>
                        </configuration>
                    </execution>
                </executions>
            </plugin>

            <!-- end::wsdl[] -->
        </plugins>
    </build>
</project>
