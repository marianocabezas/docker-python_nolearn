#
# Python + nolearn Dockerfile
# Installs all necessary tools to use Python with the nolearn package (based on Theano and Lasagne).
# This docker is useful to test deep learning approaches based on these packages.
#

FROM ubuntu:14.04

MAINTAINER Mariano Cabezas <mcabezas@eia.udg.edu>


# We add all the necessary files to the image
ADD get-pip.py /usr/local/

# We install all the necessary commands
RUN apt-get update
RUN apt-get install -y python2.7 python-dev libpng-dev libfreetype6-dev git pkg-config g++ libjpeg-dev
RUN git clone https://github.com/sergivalverde/nolearn_utils.git
RUN python /usr/local/get-pip.py
RUN pip install numpy
RUN pip install scipy
RUN cd nolearn_utils; python setup.py install
RUN cd nolearn_utils; pip install -r requirements.txt

# We prepare it to run with the images
#CMD python /usr/local/challenge/train.py
CMD python -c "import theano; print('Seems like everything is working just fine!')"
