# Copyright The PyTorch Lightning team.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

ARG PYTHON_VERSION=3.9
ARG PYTORCH_VERSION=1.8

#FROM pytorchlightning/pytorch_lightning:base-cuda-py${PYTHON_VERSION}-torch${PYTORCH_VERSION}
#FROM 
FROM rocm/pytorch:latest

LABEL maintainer="PyTorchLightning <https://github.com/PyTorchLightning>"

ARG LIGHTNING_VERSION=""

COPY ./ /home/pytorch-lightning/
RUN ls /home/pytorch-lightning/
# install dependencies
RUN \
    cd /home && \
    mv pytorch-lightning/_notebooks notebooks && \
    mv pytorch-lightning/pl_examples . && \
    #replace by specific version if asked
    if [ ! -z "$LIGHTNING_VERSION" ] ; then \
        rm -rf pytorch-lightning ; \
        wget https://github.com/PyTorchLightning/pytorch-lightning/archive/${LIGHTNING_VERSION}.zip --progress=bar:force:noscroll ; \
        unzip ${LIGHTNING_VERSION}.zip ; \
        mv pytorch-lightning-*/ pytorch-lightning ; \
        rm *.zip ; \
    fi && \
    #ls /home/pytorch-lightning/
    #python /home/pytorch-lightning/setup.py build
    #pip install ./pytorch-lightning["extra"] --no-cache-dir && \
    #rm -rf pytorch-lightning
    #PYLIGHTING BUILD HERE
    cd pytorch-lightning && \
    pip install .
    #python setup.py build
    #git clone https://github.com/Lightning-AI/lightning.git && \
    #pip install pytorch-lightning 

RUN python --version && \
    pip --version && \
    pip list && \
    ls
    #python -c "import pytorch_lightning as pl; print(pl.__version__)"
    #ENABLE TO CHECK LIGHTNING

# CMD ["/bin/bash"]