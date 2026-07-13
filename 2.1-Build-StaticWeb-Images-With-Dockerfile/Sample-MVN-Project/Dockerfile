FROM maven:3.6.3-openjdk-17
WORKDIR /mvn-app
COPY . .
RUN mvn clean
CMD ["mvn", "package"]
