# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# DO NOT EDIT THIS FILE. IT IS AUTO_GENERATED
# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
FROM cyberdojofoundation/alpine_glibc

# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# START of extra commands to fulfil runner's requirements (os=Alpine)
RUN (getent group sandbox) || (addgroup -g 51966 sandbox)
RUN (grep -q sandbox:x:41966 /etc/passwd) || (adduser -D -g "" -h /home/sandbox -G sandbox -s /bin/bash -u 41966 sandbox)
RUN apk add --update coreutils bash tar file
# END of extra commands to fulfil runner's requirements
# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

LABEL maintainer=bradcray@gmail.com

ENV CHPL_VERSION 1.23.0
ENV CHPL_HOME /opt/chapel/chapel-${CHPL_VERSION}
ENV PATH ${PATH}:${CHPL_HOME}/bin/linux64-x86_64:${CHPL_HOME}/util

RUN \
apk add ca-certificates && \
apk add bash gcc g++ make perl python wget && \
\
mkdir -p /opt/chapel && \
wget -q -O - https://github.com/chapel-lang/chapel/releases/download/${CHPL_VERSION}/chapel-${CHPL_VERSION}.tar.gz | tar -xzC /opt/chapel && \
\
/bin/bash -c "source ${CHPL_HOME}/util/quickstart/setchplenv.bash && \
cd /opt/chapel && \
make -C ${CHPL_HOME} && \
printchplenv --simple > ${CHPL_HOME}/.chplconfig" && \
\
apk del wget
