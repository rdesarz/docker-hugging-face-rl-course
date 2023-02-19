FROM nvidia/cuda:11.4.0-base-ubuntu20.04

RUN apt-get update 

RUN DEBIAN_FRONTEND=noninteractive apt-get -y install tzdata

RUN apt-get install -y python3 \
                       python3-pip \
                       git

RUN apt-get install -y python3-opengl \
                       ffmpeg \
                       xvfb

RUN apt-get install -y swig \
                       cmake \
                       freeglut3-dev

EXPOSE 8888

RUN python3 -m pip install jupyter pyvirtualdisplay pyglet==1.5.1

WORKDIR /app

RUN git clone https://github.com/DLR-RM/rl-baselines3-zoo

WORKDIR rl-baselines3-zoo

RUN python3 -m pip install -r requirements.txt

RUN apt-get install -y python 
WORKDIR /app

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser"]
