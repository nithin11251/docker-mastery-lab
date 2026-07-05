FROM ubuntu
RUN apt-get update && apt-get install -y passwd
RUN useradd -m user1
USER user1
CMD ["whoami"]
