FROM centos/httpd

ARG OS_VER
ARG AMBARI_VER
ARG HDP_VER
ARG HDP_UTILS_VER

RUN  yum install -y yum-utils createrepo wget

ENV AMBARI_REPO_URL=http://public-repo-1.hortonworks.com/ambari/centos${OS_VER}/2.x/updates/${AMBARI_VER}/ambari.repo
ENV HDP_REPO_URL=http://public-repo-1.hortonworks.com/HDP/centos${OS_VER}/2.x/updates/${HDP_VER}/hdp.repo

RUN wget -nv ${AMBARI_REPO_URL} -O /etc/yum.repos.d/ambari.repo
RUN wget -nv ${HDP_REPO_URL} -O /etc/yum.repos.d/hdp.repo

RUN mkdir -p /var/www/html/ambari/${OS_VER}
RUN mkdir -p /var/www/html/hdp/${OS_VER}

RUN reposync -p /var/www/html/ambari/${OS_VER} -r ambari-${AMBARI_VER}
RUN reposync -p /var/www/html/hdp/${OS_VER} -r HDP-${HDP_VER}
RUN reposync -p /var/www/html/hdp/${OS_VER} -r HDP-UTILS-${HDP_UTILS_VER}

RUN createrepo /var/www/html/ambari/${OS_VER}/ambari-${AMBARI_VER}
RUN createrepo /var/www/html/hdp/${OS_VER}/HDP-${HDP_VER}
RUN createrepo /var/www/html/hdp/${OS_VER}/HDP-UTILS-${HDP_UTILS_VER}
