from rojima1/dev

USER root
WORKDIR /home/root

RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install -y \
      libbz2-1.0:i386 \
      libncurses5:i386 \
      libstdc++6:i386 \
      module-init-tools \
      openjdk-8-jdk \
      zlib1g:i386

COPY NVIDIA-Linux-x86_64-381.22.run /tmp/NVIDIA.run
RUN sh /tmp/NVIDIA.run -a -N --ui=none --no-kernel-module

RUN wget -q -O android-studio.zip https://dl.google.com/dl/android/studio/ide-zips/2.3.3.0/android-studio-ide-162.4069837-linux.zip && unzip android-studio.zip && mv android-studio /opt && \
    groupadd --gid 130 kvm && \
    gpasswd -a developer kvm

USER developer
WORKDIR /home/developer

CMD /opt/android-studio/bin/studio.sh
