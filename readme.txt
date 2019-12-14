This repository contains the binary packages for instrumenting java applications v1.8 in Google Appengine Standard
In the outermost maven POM of the project include the following sections and then re"package", "install" and "deploy"
<!-- In the build section -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-dependency-plugin</artifactId>
                <version>3.1.1</version>
                <executions>
                <execution>
                <id>copy</id>
                <phase>compile</phase>
                <goals>
                    <!-- one of the two goals not both probably unpack as we can filter out-->
                    <goal>unpack</goal>
                </goals>
                <configuration>
                    <artifactItems>
                        <artifactItem>
                            <groupId>prismo.systems</groupId>
                            <artifactId>prismoservlet</artifactId>
                            <version>1.0-SNAPSHOT</version>
                            <type>jar</type>
                            <overWrite>true</overWrite>
                            <outputDirectory>${project.build.directory}/${project.build.finalName}/WEB-INF/classes</outputDirectory>
                            <includes>com/prismo/PrismoServlet.class</includes>
                        </artifactItem>
                    </artifactItems>
                </configuration>
                </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
    
   <!--Dependency section -->
   <dependencies>
    <dependency>
        <groupId>prismo.systems</groupId>
        <artifactId>prismoservlet</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>

<!-- Add "this" repository at the end of the POM before the </project>
    <repositories>
        <repository>
            <id>prismo-systems.java.master</id>
            <url>https://raw.github.com/prismo-systems/java/master/</url>
        </repository>
    </repositories>

    
