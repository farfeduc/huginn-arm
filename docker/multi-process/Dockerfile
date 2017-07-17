FROM armhf/ubuntu

ADD docker/scripts/prepare /scripts/prepare
RUN chmod +x /scripts/prepare && sh /scripts/prepare

ADD docker/multi-process/scripts/standalone-packages /scripts/standalone-packages
RUN chmod +x /scripts/prepare && sh /scripts/standalone-packages

WORKDIR /app

ADD ["Gemfile", "Gemfile.lock", "/app/"]
ADD lib/gemfile_helper.rb /app/lib/
ADD vendor/gems /app/vendor/gems

RUN chown -R huginn:huginn /app && \
    sudo -u huginn -H echo "gem 'sqlite3', '~> 1.3.11'" >> /app/Gemfile && \
    sudo -u huginn -H LC_ALL=en_US.UTF-8 RAILS_ENV=production ON_HEROKU=true bundle install --without test development --path vendor/bundle -j 4
COPY . /app

ARG OUTDATED_DOCKER_IMAGE_NAMESPACE=false
ENV OUTDATED_DOCKER_IMAGE_NAMESPACE ${OUTDATED_DOCKER_IMAGE_NAMESPACE}

ADD ["docker/scripts/setup", "docker/scripts/setup_env", "docker/multi-process/scripts/init", "/scripts/"]

RUN chmod +x /scripts/prepare && sh /scripts/setup

VOLUME /var/lib/mysql

EXPOSE 3000

CMD ["/scripts/init"]

