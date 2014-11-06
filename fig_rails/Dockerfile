FROM ruby:2.1

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev

# Gemfileをローカルから入れる
RUN mkdir /myapp
WORKDIR /myapp
#ADD ./Gemfile /myapp/Gemfile
#RUN bundle install

# カレントディレクトリをvmの/myappとしてマウント
ADD . /myapp
# キャッシュしたい
RUN bundle install
