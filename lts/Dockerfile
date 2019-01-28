FROM sonarqube:6.7.5

MAINTAINER Tim Taylor <mpx1@cdc.gov, ttaylor@mitre.org>

LABEL io.k8s.description="SonarQube image that will run in OpenShift with restricted SCC" \
    io.k8s.display-name="SonarQube (LTS)" \
    io.openshift.tags="sonarqube,sonarqube-lts" \
    io.openshift.expose-services="9000:http"

USER 0
# Replace original run.sh with our custom one
COPY run.sh $SONARQUBE_HOME/bin/
RUN chmod +x $SONARQUBE_HOME/bin/run.sh && \
    chown -R sonarqube:root $SONARQUBE_HOME && \
    chmod -R 0775 $SONARQUBE_HOME/data && \
    chmod -R 0775 $SONARQUBE_HOME/extensions && \
    chmod -R 0775 $SONARAQUBE_HOME/logs && \
    chmod -R 0775 $SONARQUBE_HOME/temp

USER 1001
