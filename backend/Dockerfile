FROM openjdk:8

# Install dependencies
ENV DEBIAN_FRONTEND noninteractive
ENV JAVA_OPTS -verbose:gc -Xms1G -Xmx1G

RUN apt-get update && \
  apt-get install -qq -y git ca-certificates

RUN java -version
RUN javac -version

RUN apt-get remove scala-library scala
RUN wget https://scala-lang.org/files/archive/scala-2.11.8.deb
RUN dpkg -i scala-2.11.8.deb

RUN wget https://dl.bintray.com/sbt/debian/sbt-1.1.2.deb
RUN dpkg -i sbt-1.1.2.deb

# Grab the checked out source
RUN git clone https://github.com/WikiPlagSS2018/wikiplag-multi server

WORKDIR /server

COPY ./app.conf /server/restApi/src/main/resources/app.conf

RUN sbt "exit"

CMD ["sbt", "; project restApi; jetty:start"]
