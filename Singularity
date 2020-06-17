Bootstrap: localimage
From: ../../simgs/base.simg

%environment
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
    export LD_LIBRARY_PATH
    CUDA_HOME=/usr/local/cuda
    export CUDA_HOME
    LC_ALL=C
    export LC_ALL
    GEOMSTATS_BACKEND=numpy
    export GEOMSTATS_BACKEND

%post
    pip3 install pip==9.0.1
    apt-get install curl
    curl http://neuro.debian.net/lists/xenial.de-m.full | tee /etc/apt/sources.list.d/neurodebian.sources.list
    apt-get update
    pip3 install --upgrade setuptools
    pip3 install git+git://github.com/geomstats/geomstats.git@nina-s2-pytorch
    pip3 install --upgrade git+git://github.com/hyperopt/hyperopt.git
    pip3 install jinja2 \
                 joblib \
                 luigi \
                 nibabel \
                 nilearn \
                 numpy==1.15.1 \
                 psutil \
                 ray \
                 scikit-image \
                 scikit-learn \
                 seaborn \
                 setproctitle \
                 sympy \
                 torch==1.0.1 \
                 torchvision \
                 visdom


%runscript
    exec /usr/bin/python3 -u ray_pipeline.py
