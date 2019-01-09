# Run a salt-ssh in a container.
#
# docker run --rm -it -v $(pwd)/roster:/etc/salt/roster jweinstock/salt-ssh
#
# Run salt-ssh commands:
# salt-ssh -i 'entry_in_roster' state.apply docker.host
# salt-ssh -i 'entry_in_roster' state.apply docker.client.container
FROM alpine:3.6
LABEL forked_from "Jacob Weinstock <jakobweinstock@gmail.com>"
LABEL maintainer "mxrss"


ENV DEPS salt-ssh==2018.3.1 pyopenssl==18.0.0
ENV PYTHON_VERSION 2.7.15-r0
# install musl-dev gcc as dependencies for installing gevent
RUN apk --no-cache --update add python2=${PYTHON_VERSION} openssl openssh py2-pip \
    && apk add --virtual build-dependencies python2-dev=${PYTHON_VERSION} musl-dev gcc libffi-dev openssl-dev  \
    && pip install --no-cache-dir ${DEPS} 


RUN  apk --purge del build-dependencies \
   && rm -rf /var/cache/apk/* /root/.cache \
   && mkdir -p /srv/salt

ADD ./entrypoint.sh /


CMD ["/bin/sh", "/entrypoint.sh"]