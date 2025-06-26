# FROM jupyter/scipy-notebook
# FROM jupyter/base-notebook
# FROM jupyter/scipy-notebook:b2562c469cdd
FROM jupyter/datascience-notebook
# FROM python:3.12

USER root

#RUN apt install gcc

#RUN wget https://github.com/ta-lib/ta-lib/releases/download/v0.6.4/ta-lib-0.6.4-src.tar.gz \
#    tar -xzf ta-lib-0.6.4-src.tar.gz \
#    cd ta-lib-0.6.4/ \
#    ./configure --prefix=/usr \
#    make \
#    sudo make install \

COPY requirements.txt /tmp/

RUN pip install --requirement /tmp/requirements.txt && \
#    fix-permissions $CONDA_DIR && \
#    fix-permissions /home/$NB_USER && \
    apt update && \
    apt-get install curl -y && \
    export NODE_OPTIONS=--max-old-space-size=4096 &&\
#    jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build &&\
#    jupyter labextension install jupyterlab-plotly --no-build &&\
#    jupyter labextension install plotlywidget --no-build &&\
#    # jupyter labextension install qgrid2 --no-build &&\ # not working
#    jupyter labextension install jupyterlab-chart-editor --no-build &&\  # adding this breaks the above stuff. But individually this works.
#    jupyter labextension install jupyterlab-dash &&\
#    jupyter lab build &&\
    unset NODE_OPTIONS

#RUN conda install -c conda-forge ta-lib -y

ENV PYTHONPATH "${PYTHONPATH}:/home/project/work/q_pack"
ENV JUPYTER_ENABLE_LAB "yes"
    
CMD ["jupyter", "lab", "--no-browser","--NotebookApp.token=''","--NotebookApp.password=''", "--allow-root"]


# Another way to give root access without password in the compose
    # environment:
    #   GRANT_SUDO: "yes"
    # user:
    #   "root"