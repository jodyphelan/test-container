FROM mcr.microsoft.com/devcontainers/miniconda:0-3

# Copy environment.yml (if found) to a temp location so we update the environment. Also
# copy "noop.txt" so the COPY instruction does not fail if no environment.yml exists.
COPY environment.yml* .devcontainer/noop.txt /tmp/conda-tmp/
RUN if [ -f "/tmp/conda-tmp/environment.yml" ]; then umask 0002 && /opt/conda/bin/conda env update -n base -f /tmp/conda-tmp/environment.yml; fi \
    && rm -rf /tmp/conda-tmp

RUN /opt/conda/bin/conda config --add channels defaults  \
    && /opt/conda/bin/conda config --add channels bioconda \
    && /opt/conda/bin/conda config --add channels conda-forge \
    && /opt/conda/bin/conda config --set channel_priority strict \
    && /opt/conda/bin/conda config --set solver libmamba 

# cd to /workspaces
WORKDIR /workspaces

RUN wget https://raw.githubusercontent.com/jodyphelan/genomics_course/master/conda_env/mapping.explicit.txt \
    && /opt/conda/bin/conda create --name mapping --file mapping.explicit.txt \
    && rm mapping.explicit.txt


RUN apt-get update && export DEBIAN_FRONTEND=noninteractive && apt-get install -y firefox-esr
# [Optional] Uncomment to install a different version of Python than the default
# RUN conda install -y python=3.6 \
#     && pip install --no-cache-dir pipx \
#     && pipx reinstall-all

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
