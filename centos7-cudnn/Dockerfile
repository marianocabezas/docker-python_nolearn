#
# Python + nolearn Dockerfile
# Installs all necessary tools to use Python with the nolearn package (based on Theano and Lasagne).
# This docker is useful to test deep learning approaches based on these packages.
#

FROM nvidia/cuda:7.5-cudnn5-devel-centos7

MAINTAINER Mariano Cabezas <mcabezas@eia.udg.edu>


# We add all the necessary files to the image
ADD get-pip.py /usr/local/

# We install all the necessary commands
RUN yum install -y git gcc-c++ python-devel freetype-devel zlib-devel libjpeg-devel libpng12-devel
RUN git clone https://github.com/sergivalverde/nolearn_utils.git
RUN python /usr/local/get-pip.py
RUN pip install numpy
RUN pip install scipy
RUN cd nolearn_utils; python setup.py install
RUN cd nolearn_utils; pip install -r requirements.txt

# We prepare it to run with the images
CMD python -c "import theano; print('Seems like everything is working just fine!')"
