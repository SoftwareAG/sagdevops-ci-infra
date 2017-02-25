# base Command Central server image
FROM sagdevops/cce:9.12

ADD . /src
WORKDIR /src

# start tooling, apply template(s), cleanup
RUN /sag/profiles/SPM/bin/startup.sh && /sag/profiles/CCE/bin/startup.sh && \
    sagccant connectmirrors deployer stopcc -Denv=dockerfile && \
    cd /sag && rm -fr /tmp/* common/conf/nodeId.txt profiles/SPM/logs/* profiles/CCE

# SPM ports
EXPOSE 8092 8093

# IS ports 
EXPOSE 8094 8095

# start SPM and then Deployer IS
CMD $SAG_HOME/profiles/SPM/bin/startup.sh && $SAG_HOME/profiles/IS_deployer/bin/console.sh
