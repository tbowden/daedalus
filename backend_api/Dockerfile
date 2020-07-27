FROM ubuntu:18.04 as dev

# Use ubuntugis unstable
RUN apt-get update && apt-get install -y --no-install-recommends \
  gnupg \
  gosu \
  python3 python3-dev \
  software-properties-common \
  tzdata \
  vim \
  && add-apt-repository ppa:ubuntugis/ubuntugis-unstable \
  && apt-key adv --keyserver keyserver.ubuntu.com --recv-key 51F523511C7028C3 \
  && echo 'deb https://qgis.org/ubuntugis bionic main' >> /etc/apt/sources.list.d/qgis.list \
  && echo 'deb-src https://qgis.org/ubuntugis bionic main' >> /etc/apt/sources.list.d/qgis.list \
  && apt-get update

RUN apt-get install -y --no-install-recommends python3-pip
RUN apt-get install -y --no-install-recommends python3-venv

ENV VIRTUAL_ENV=/usr/local/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

#RUN pip install minimal
COPY requirements.txt .
RUN pip install -r requirements.txt

RUN adduser --gecos app --disabled-password app

USER app


