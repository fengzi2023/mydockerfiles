FROM jupyter/scipy-notebook:6c3390a9292e

LABEL maintainer="fengyuwei <fengyuwei01@gmail.com>"

USER $NB_UID

RUN conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ && \
    conda config --set show_channel_urls yes && \
    conda create --quiet --yes -p $CONDA_DIR/envs/python2 python=2 \
        'ipywidgets=6.0*' \
        'kernda=0.3*' \
        'ipykernel=4.6*' \
        'numpy=1.13*' \
        'pandas=0.20*' \
        'scipy=0.19*' \
        'matplotlib=2.0*' \
        'scikit-learn=0.19*' && \
    conda clean --all -f -y

USER root

RUN $CONDA_DIR/envs/python2/bin/python -m ipykernel install && \
    $CONDA_DIR/envs/python2/bin/kernda -o -y /usr/local/share/jupyter/kernels/python2/kernel.json && \
    ln -s $CONDA_DIR/envs/python2/bin/pip $CONDA_DIR/bin/pip2 && \
    ln -s $CONDA_DIR/bin/pip $CONDA_DIR/bin/pip3

USER $NB_UID
