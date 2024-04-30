FROM mcr.microsoft.com/devcontainers/miniconda:0-3


RUN /opt/conda/bin/conda config --add channels defaults  \
    && /opt/conda/bin/conda config --add channels bioconda \
    && /opt/conda/bin/conda config --add channels conda-forge \
    && /opt/conda/bin/conda config --set channel_priority strict \
    && /opt/conda/bin/conda config --set solver libmamba 


COPY env.txt /tmp/conda-tmp/

RUN /opt/conda/bin/conda create --name mapping --file /tmp/conda-tmp/env.txt


# cd to /workspaces
# WORKDIR /workspaces


# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive && apt-get install -y firefox-esr
# [Optional] Uncomment to install a different version of Python than the default
# RUN conda install -y python=3.6 \
#     && pip install --no-cache-dir pipx \
#     && pipx reinstall-all

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
