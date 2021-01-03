# for build run 
# docker build -t returntowhat:downunderctf . 
# 
# run in linux or macos
# sudo docker run --rm -v --cap-add=SYS_PTRACE -p 1337:1337 -d --name returntowhat -i returntowhat:downunderctf

FROM ubuntu:18.04

RUN apt-get update && apt-get -y install socat
RUN useradd -d /home/ductf/ -m -p ductf -s /bin/bash ductf
RUN echo "ductf:ductf" | chpasswd
RUN mkdir /home/ductf/challenge



COPY challenge/return-to-what /home/ductf/challenge
COPY challenge/flag.txt /home/ductf/challenge
RUN chown -R root:root /home/ductf

WORKDIR /home/ductf/challenge
EXPOSE 1337

CMD ["socat", "-T60", "TCP-LISTEN:1337,reuseaddr,fork,su=ductf","EXEC:/home/ductf/challenge/return-to-what"]
