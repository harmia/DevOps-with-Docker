FROM ruby:2.6.0

WORKDIR /usr/app

COPY ./ ./

RUN gem install bundler

RUN bundle install

RUN apt-get update && apt-get install -y nodejs

RUN rails db:migrate

CMD rails s

EXPOSE 3000
