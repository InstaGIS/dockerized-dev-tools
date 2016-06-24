FROM ubuntu:16.04

ARG user=instauser
ARG user_uid=1000
ARG user_home_dir=/home/$user

# Install base packages
RUN apt-get update && apt-get install -y --no-install-recommends \
	ca-certificates \
	lsb-release \
	sudo \
	wget

# Setup PostgreSQL APT repository
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" | tee /etc/apt/sources.list.d/pgdg.list
RUN wget -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -

# Install application packages
RUN apt-get update && apt-get install -y --no-install-recommends \
	build-essential \
	libpq-dev \
	postgresql-client-9.5 \
	python3 \
	python3-dev

# Set Python 3 as default Python
RUN ln -s /usr/bin/python3 /usr/local/bin/python

# Install pip
RUN wget -O - https://bootstrap.pypa.io/get-pip.py | python3

# Install Python requirements
RUN pip3 install \
	ipython==4.2.0 \
	psycopg2==2.6.1 \
	virtualenvwrapper==4.7.1

# Setup standard user account
RUN adduser --home $user_home_dir --uid $user_uid --disabled-password --gecos "" $user && \
    addgroup $user sudo && \
    passwd --delete $user

USER $user

# Setup shell
ENV force_color_prompt yes
RUN echo ". /usr/local/bin/virtualenvwrapper.sh" >> $user_home_dir/.bashrc

WORKDIR $user_home_dir
