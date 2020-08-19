ARG userid=1000
ARG username=clang

FROM ubuntu

RUN apt-get -y update && \
    apt-get -y install wget ca-certificates gnupg

RUN echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-11 main" >> /etc/apt/sources.list && \
    echo "deb-src http://apt.llvm.org/focal/ llvm-toolchain-focal-11 main" >> /etc/apt/sources.list && \
    wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add - && \
    apt-get -y update

RUN apt-get -y install clang-11 gcc-10

RUN apt-get -y remove wget ca-certificates gnupg && \
    apt-get -y autoremove && \
    apt-get -y clean

RUN groupadd -g $userid $username && \
    useradd -u $userid -g $username $username

USER clang

WORKDIR /home/$username

ENTRYPOINT ["clang++-11"]
