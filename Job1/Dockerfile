FROM openjdk
COPY ./petclinic*.jar /var/petclinic/petclinic.jar
CMD /usr/bin/java -Dspring.profiles.active=mysql -jar /var/petclinic/petclinic.jar --server.port=80
EXPOSE 80