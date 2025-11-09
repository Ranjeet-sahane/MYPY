# Use official Tomcat base image
FROM tomcat:9.0-jdk17-temurin

LABEL maintainer="yourname@example.com"

# Remove default webapps (optional clean setup)
RUN rm -rf /usr/local/tomcat/webapps/*

# Change Tomcat port from 8080 to 8082
RUN sed -i 's/port="8080"/port="8082"/' /usr/local/tomcat/conf/server.xml

# Copy the Maven-built WAR file into Tomcat as ROOT.war
# (Assumes mvn clean package created target/myapp.war)
COPY target/*.war /usr/local/tomcat/webapps/ROOT.war

# Optional: Add a basic HTML fallback homepage
# (this will be used if WAR doesn’t deploy immediately)
RUN mkdir -p /usr/local/tomcat/webapps/ROOT
COPY index.html /usr/local/tomcat/webapps/ROOT/index.html

# Expose the new port
EXPOSE 8082

# Start Tomcat
CMD ["catalina.sh", "run"]

