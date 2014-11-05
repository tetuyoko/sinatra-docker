FROM ubuntu:14.04 
MAINTAINER tetuyoko "tyokoyama@gmail.com"

# Install packages for building ruby
RUN apt-get update
RUN apt-get install -y --force-yes wget git libssl-dev
RUN apt-get install -y --force-yes build-essential wget git
RUN apt-get install -y --force-yes zlib1g-dev libssl-dev libreadline-dev libyaml-dev libxml2-dev libxslt-dev
RUN apt-get install -y --force-yes libreadline6 libreadline6-dev
RUN apt-get install -y --force-yes curl
RUN apt-get clean

RUN useradd -k /etc/skel -m docker
RUN echo 'docker:docker' |chpasswd

## Install ruby
RUN git clone git://github.com/sstephenson/rbenv.git /usr/local/rbenv
RUN mkdir -p /usr/local/rbenv/plugins
RUN git clone https://github.com/sstephenson/ruby-build.git /usr/local/rbenv/plugins/ruby-build
RUN /usr/local/rbenv/plugins/ruby-build/install.sh
ENV PATH /usr/local/rbenv/bin:$PATH
ENV RBENV_ROOT /usr/local/rbenv

RUN echo 'ENV RBENV_ROOT /usr/local/rbenv' >> /etc/profile.d/rbenv.sh
RUN echo 'export PATH=/usr/local/rbenv/bin:$PATH' >> /etc/profile.d/rbenv.sh
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
RUN echo 'ENV RBENV_ROOT /usr/local/rbenv'
RUN echo 'export PATH=/usr/local/rbenv/bin:$PATH' >> .bashrc
RUN echo 'eval "$(rbenv init -)"' >> .bashrc
RUN eval "$(rbenv init -)"

ENV CONFIGURE_OPTS --disable-install-doc

RUN rbenv install 2.1.2

RUN bash -l -c 'rbenv global 2.1.2'
RUN bash -l -c 'gem install bundler'
RUN bash -l -c 'gem install foreman'

#RUN bash -l -c 'rbenv rehash'
#RUN bash -l -c 'bundle'

# Install bundler
 #RUN bash -l -c 'gem update --system'
#RUN gem install bundler

# Clone sinatra app 
RUN git clone https://github.com/tcnksm/docker-sinatra /root/sinatra
RUN cd /root/sinatra;
#RUN echo 'ENV RBENV_ROOT /usr/local/rbenv' >> /etc/profile.d/rbenv.sh
#RUN bash -l -c 'bundle'

# Set run command
EXPOSE 4567
CMD ["/usr/local/rbenv/shims/foreman","start","-d","/root/sinatra"]
