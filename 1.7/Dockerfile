FROM ubuntu

RUN apt-get update && apt-get install -y curl
COPY script.sh .

CMD ["/bin/bash", "./script.sh"]
