# Jenkins 2.479
FROM jenkins/jenkins:2.479

# 환경 설정 

# 홈 디렉토리
VOLUME /data/shell_code/jenkins/jenkins_home

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli --verbose --plugin-file /usr/share/jenkins/ref/plugins.txt

# Web UI, Agent
EXPOSE 8080 50000

ENV TZ Asia/Seoul
