FROM nginx

RUN apt-get -y update
RUN apt-get -y install ruby ruby-dev make gcc nodejs

RUN gem install bundler

COPY conf/nginx.conf /etc/nginx

RUN mkdir /src

ADD src /src

WORKDIR /src

RUN bundle install

RUN bundle exec middleman build ENV=production

RUN cp -r build/* /usr/share/nginx/html

