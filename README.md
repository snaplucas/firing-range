# What is Firing Range?

Firing Range is a test bed for web application security scanners,
providing synthetic, wide coverage for an array of vulnerabilities.

It can be deployed as a Google App Engine application. A public instance
is running at https://public-firing-range.appspot.com.

# Local installation instructions (using maven)

(In the case you don't have maven installed in your machine it can be done following the steps on Install maven following the instructions on https://maven.apache.org/install.html)


1. `mkdir github && cd github`
1. `git clone https://github.com/google/firing-range.git`
1. `cd firing-range`
1. In the file pom.xml make sure that the appengine-maven-plugin is configured with you projectId (inside `<appId>` tag)
    ```
    <plugin>
        <groupId>com.google.appengine</groupId>
        <artifactId>appengine-maven-plugin</artifactId>
        <version>1.9.63</version>
        <configuration>
            <appId>public-firing-range</appId> <!-- Override appengine-web.xml <project> -->
            <version>1</version>
            <fullScanSeconds>1</fullScanSeconds>
            <retainUploadDir>true</retainUploadDir>
        </configuration>
    </plugin> 
1. In the file `appengine-web.xml` the ` <application>` tag must point to your project
    ```
    <application>public-firing-range</application>

1. `mvn clean package -DskiptTests`
1. `mvn appengine:update -DskipTests`

The application then will be run locally at http://localhost:8080

# License information

See the LICENSE file.
