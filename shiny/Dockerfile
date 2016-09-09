# our R base image
FROM rocker/shiny:latest 

MAINTAINER Evgeni Maksimov "em@aistinvest.ru"

# install additional packages
RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libxml2-dev \
    libmariadb-client-lgpl-dev \
    libssl-dev

# install additional R packages
RUN R -e "install.packages(c('magrittr', 'tidyr', 'quantmod', 'PerformanceAnalytics', 'plotly'), dependencies=TRUE)" && \
    R -e "install.packages('rusquant', repos='http://r-forge.r-project.org', dependencies=TRUE)"

# copy shiny-server.conf
COPY shiny-server.conf  /etc/shiny-server/shiny-server.conf

# set the command
CMD ["/usr/bin/shiny-server.sh"]