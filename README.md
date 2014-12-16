Product: Integration tests for WSO2 ESB Stripe connector
Pre-requisites:

- Maven 3.x
- Java 1.6 or above

Tested Platform: 

- Mac OSx 10.9
- WSO2 ESB wso2esb-4.9.0-SNAPSHOT
- Java 1.7

STEPS:

1. Make sure the wso2esb-4.9.0-SNAPSHOT.zip file at "stripe/repository/".

2. Add following code block, just after the listeners block (Remove or comment all the other test blocks) in following file - "stripe/src/test/resources/testng.xml"

	<test name="Stripe-Connector-Test" preserve-order="true" verbose="2">
        <packages>
            <package name="org.wso2.carbon.connector.integration.test.stripe"/>
        </packages>
    </test> 

3. Copy proxy files to following location "stripe/src/test/resources/artifacts/ESB/config/proxies/stripe/"

4. Copy request files to following "stripe/src/test/resources/artifacts/ESB/config/restRequests/stripe/"

5. Edit the "stripe.properties" at stripe/src/test/resources/artifacts/connector/config/ using valid and relevant data. Parameters to be changed are mentioned below.

	- proxyDirectoryRelativePath: relative path of the rest request files folder from target.
	- requestDirectoryRelativePath: relative path of proxy folder from target.
	- propertiesFilePath: relative path of properties file from target.
    - clientSecret: to get the access token for a particular client_secret.
	- refreshToken: refresh token to get the access token.
	- apiUrl: API URL.
		
6. Following data set can be used for the first testsuite run.

		proxyDirectoryRelativePath=/../src/test/resources/artifacts/ESB/config/proxies/stripe/
		requestDirectoryRelativePath=/../src/test/resources/artifacts/ESB/config/restRequests/stripe/
		propertiesFilePath=/../src/test/resources/artifacts/ESB/connector/config/
 		refreshToken=rt_5KeYCAqc76HbrUx5RVfJEGt3xCRHZrXZOSoXGNna57DC4JNf
		clientSecret=sk_test_Gd3JGidPIzfPkMOC8ZGnPEdf
        apiUrl=https://api.stripe.com
        apiVersion=v1

7. Required to change on test
	change the relevant data in the corresponding text file(Text files in the rest requests folder)

8. Navigate to "stripe/" and run the following command.
     $ mvn clean install