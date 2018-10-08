# PCF-SpringBoot

This respository has 3 projects specific to Pivotal Cloud Foundry

SpringCloud MultidataSource connects to 2 datasource one RDBMS and other MongoDb

SpringCloudPCFFeignServer which use PCF service discovery service .Please go through the pom.xml to look for PCF dependencies needed for Service Discovery.Note Springboot1.5 is used here. 

Listed below are the dependencies eesential for service discovery in Cloud Foundry

<dependency>
            <groupId>io.pivotal.spring.cloud</groupId>
            <artifactId>spring-cloud-services-starter-service-registry</artifactId>
        </dependency>
		<dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-spring-service-connector</artifactId>
        </dependency>
		 <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>io.pivotal.spring.cloud</groupId>
                <artifactId>spring-cloud-services-dependencies</artifactId>
                <version>1.1.1.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Camden.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>


SpringCloudPCFFeignClient is PCF service discovery service and is consumer of services provided by SpringCloudPCFFeignServer .The service /notify/{user}(SpringCloudPCFFeignClient) calls service  /message/{user}(SpringCloudPCFFeignServer) to get list of messages for a user to show the notification messages
