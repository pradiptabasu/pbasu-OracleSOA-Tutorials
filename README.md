# pbasu-OracleSOA-Tutorials

__**Processing No Namespace XML Messages SOA 11g**__
* http://sathyam-soa.blogspot.com/2013/11/processing-no-namespace-xml-messages.html
* http://soacrux.blogspot.com/2010/12/processing-xml-input-without-namespace.html
* 
* 
* 

* https://technology.amis.nl/2015/11/27/processing-large-xml-files-in-the-soa-suite/
* http://www.ateam-oracle.com/rest-adapter-and-json-translator-in-soaosb-12-1-3-2
* http://yatanveersingh.blogspot.com/2010/06/reading-xml-file-using-file-adapter-in.html
* 
* 

__**Dynamic Credential & Dynamic Endpoint**__
* https://www.baigzeeshan.com/2015/10/how-to-pass-dynamic-credentials-to-web.html
* https://www.oracle.com/technetwork/topics/soa/dynamic-endpoints-100390.html
* http://oraclesoasuitetips.blogspot.com/2014/08/dynamically-setting-csf-key.html
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec70/adding-keys-to-a-credential-store
* https://community.oracle.com/thread/2622139
* http://soa-howto.blogspot.com/2008/09/how-to-set-security-credentials.html
* http://ofmxperts.blogspot.com/2011/12/how-to-set-security-credentials.html
* https://dzone.com/articles/get-credential-store-framework-key-inside-soa-comp
* http://biemond.blogspot.com/2010/08/http-basic-authentication-with-soa.html
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec71/invoking-an-http-basic-secured-web-service
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec67/restricting-a-composite-to-authenticated-users-with-http-basic-security
* https://stackoverflow.com/questions/47081479/bpel-12c-call-webservices-with-basic-authentication
* https://blogs.oracle.com/ardaeralp/bpel-calling-web-services-with-http-basic-authentication
* https://community.oracle.com/thread/1013997
* https://www.albinsblog.com/2012/06/invoking-web-service-from-composite.html#.XMiRE2gzbIU
* http://oraclesoasuitetips.blogspot.com/2014/08/dynamically-setting-csf-key.html
* 
* 

__**Dynamic Variable values which changes with environment**__
* https://sswaro.wordpress.com/handle-dynamic-parameter-using-bpel-preference-property/
* http://learn-oraclesoa.blogspot.com/2013/05/setting-and-getting-preferences-soa.html
* https://technology.amis.nl/2008/01/06/oracle-bpel-process-manager-most-efficient-way-to-manage-dynamic-process-level-cross-instance-data/
* https://intelligentpathways.com.au/blog/soa-environment-reference-deployment-approaches/
* https://osb11g.blogspot.com/2016/06/soa-using-oragetpreference-in-bpel.html
* 
* 

__**Opaque Schema**__
* https://technology.amis.nl/2014/08/06/opaque-does-not-mean-just-pass-anything-in-it-has-to-be-base64-jca-adapters/
* https://redthunder.blog/2016/11/22/teaching-how-to-use-the-oracle-osbsoa-jms-adapter-bpel-and-mediator/
* https://blogs.oracle.com/fusionmiddlewaresupport/jms-step-4-how-to-create-an-11g-bpel-process-which-writes-a-message-based-on-an-xml-schema-to-a-jms-queue-v2
* http://oraclefuzion.blogspot.com/2011/02/reading-opaque-data-in-bpel.html
* https://www.tavant.com/blog/osb-tip-proxy-service-which-can-take-any-xml-data-any-jms-queue-oracle-service-bus
* 
* 

__** One-way & Two-way SSL Setup**__
* https://technology.amis.nl/2014/08/17/soa-suite-12c-configuring-gmail-as-the-inbound-email-provider-for-ums-imap-ssl/
* https://technology.amis.nl/2014/08/05/setup-gmail-as-mail-provider-for-soa-suite-12c-configure-smtp-certificate-in-trust-store/
* https://technology.amis.nl/2019/03/24/running-apache-kafka-on-minikube/
* https://javaoraclesoa.blogspot.com/2017/05/oracle-soa-suite-two-way-ssl-with-tls12.html
* https://svgonugu.com/2015/03/06/service-bus-12c-outbound-ssl/
* 
* 
openssl s_client -connect imap.gmail.com:993 > gmail-imap-cert.pem
Open the file you retrieved with OpenSSL – gmail-imap-cert.pem in my case – in an editor (such as vi).

Remove all the lines before the line that says —–BEGIN CERTIFICATE—– – but leave this line itself! Also remove all lines after the line with —–END CERTIFICATE—– but again, leave this line itself. Save the resulting file, for example as gmail-imp-certificate.txt (but you can pick any name you like).

WebLogic (on which SOA Suite is running) out of the default installation uses a special keystore. It does not use the cacerts store that is installed with the JDK or JRE but instead uses a file called DemoTrust.jks and typically located at %WL_HOME/server/lib/DemoTrust.jks. This trust store is “injected” into the JVM when the WebLogic domain is started: “-Djavax.net.ssl.trustStore=/opt/oracle/middleware12c/wlserver/server/lib/DemoTrust.jks”. We have the option of removing this start up parameter: remove “-Djavax.net.ssl.trustStore=%WL_HOME%\server\lib\DemoTrust.jks” in setDomainEnv.cmd  and then add the certificates to the default Java keystore (cacerts) or, the easier option, we can add the certificate to the DemoTrust keystore that WebLogic uses.

The command for doing this, looks as follows, in my environment at least:

/usr/java/latest/jre/bin/./keytool -import -alias imap.gmail.com -keystore /opt/oracle/middleware12c/wlserver/server/lib/DemoTrust.jks -file /var/log/weblogic/gmail-imap-certificate.txt


The default password for the keystore is DemoTrustKeyStorePassPhrase.

You will be asked explicitly whether you trust this certificate [and are certain about adding it to the keystore]. Obviously you will have to type y in order to confirm the addition to the keystore:



