# Diastaticus_genomes
Research done under Dr. Becket &amp; Dr. Read on identifying multiple strains of Diastaticus yeast.

Waiting for build to start...
Picked Git content provider.
Cloning into '/tmp/repo2dockerqd2v8h21'...
HEAD is now at 768ae83 Create .bashrc
Building conda environment for python=3.7Using PythonBuildPack builder
Building conda environment for python=3.7Building conda environment for python=3.7Step 1/46 : FROM buildpack-deps:bionic
 ---> 45b76b488328
Step 2/46 : ENV DEBIAN_FRONTEND=noninteractive
 ---> Using cache
 ---> 04177803d455
Step 3/46 : RUN apt-get -qq update &&     apt-get -qq install --yes --no-install-recommends locales > /dev/null &&     apt-get -qq purge &&     apt-get -qq clean &&     rm -rf /var/lib/apt/lists/*
 ---> Using cache
 ---> 59956aac2210
Step 4/46 : RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen &&     locale-gen
 ---> Using cache
 ---> 7a60c435a28a
Step 5/46 : ENV LC_ALL en_US.UTF-8
 ---> Using cache
 ---> b272dca96c21
Step 6/46 : ENV LANG en_US.UTF-8
 ---> Using cache
 ---> df235fcbbf57
Step 7/46 : ENV LANGUAGE en_US.UTF-8
 ---> Using cache
 ---> c759b467672e
Step 8/46 : ENV SHELL /bin/bash
 ---> Using cache
 ---> 8eeca7e9cef2
Step 9/46 : ARG NB_USER
 ---> Using cache
 ---> 41e637cf5b01
Step 10/46 : ARG NB_UID
 ---> Using cache
 ---> 41f5f8a042a8
Step 11/46 : ENV USER ${NB_USER}
 ---> Using cache
 ---> fb096594f3bb
Step 12/46 : ENV HOME /home/${NB_USER}
 ---> Using cache
 ---> bf4574cea373
Step 13/46 : RUN groupadd         --gid ${NB_UID}         ${NB_USER} &&     useradd         --comment "Default user"         --create-home         --gid ${NB_UID}         --no-log-init         --shell /bin/bash         --uid ${NB_UID}         ${NB_USER}
 ---> Using cache
 ---> 5335cdfd3f9e
Step 14/46 : RUN wget --quiet -O - https://deb.nodesource.com/gpgkey/nodesource.gpg.key |  apt-key add - &&     DISTRO="bionic" &&     echo "deb https://deb.nodesource.com/node_10.x $DISTRO main" >> /etc/apt/sources.list.d/nodesource.list &&     echo "deb-src https://deb.nodesource.com/node_10.x $DISTRO main" >> /etc/apt/sources.list.d/nodesource.list
 ---> Using cache
 ---> 6a843c1629cd
Step 15/46 : RUN apt-get -qq update &&     apt-get -qq install --yes --no-install-recommends   less        nodejs        unzip        > /dev/null &&     apt-get -qq purge &&     apt-get -qq clean &&     rm -rf /var/lib/apt/lists/*
 ---> Using cache
 ---> 9319a43cade7
Step 16/46 : EXPOSE 8888
 ---> Using cache
 ---> bc58740f2366
Step 17/46 : ENV APP_BASE /srv
 ---> Using cache
 ---> 1eabd83d81a5
Step 18/46 : ENV NPM_DIR ${APP_BASE}/npm
 ---> Using cache
 ---> 74fb03602aa2
Step 19/46 : ENV NPM_CONFIG_GLOBALCONFIG ${NPM_DIR}/npmrc
 ---> Using cache
 ---> 28e986551940
Step 20/46 : ENV CONDA_DIR ${APP_BASE}/conda
 ---> Using cache
 ---> b480394147c4
Step 21/46 : ENV NB_PYTHON_PREFIX ${CONDA_DIR}/envs/notebook
 ---> Using cache
 ---> 315176ab7428
Step 22/46 : ENV KERNEL_PYTHON_PREFIX ${NB_PYTHON_PREFIX}
 ---> Using cache
 ---> 6f16af509827
Step 23/46 : ENV PATH ${NB_PYTHON_PREFIX}/bin:${CONDA_DIR}/bin:${NPM_DIR}/bin:${PATH}
 ---> Using cache
 ---> 5e2d228dc15f
Step 24/46 : COPY build_script_files/-2fusr-2flib-2fpython3-2e6-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2factivate-2dconda-2esh-2747be /etc/profile.d/activate-conda.sh
 ---> Using cache
 ---> acbf517f82ce
Step 25/46 : COPY build_script_files/-2fusr-2flib-2fpython3-2e6-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2fenvironment-2epy-2d3-2e7-2efrozen-2eyml-b3d5bc /tmp/environment.yml
 ---> Using cache
 ---> 211b33b322d9
Step 26/46 : COPY build_script_files/-2fusr-2flib-2fpython3-2e6-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2finstall-2dminiforge-2ebash-76fdcd /tmp/install-miniforge.bash
 ---> Using cache
 ---> dd3ab610b42d
Step 27/46 : RUN mkdir -p ${NPM_DIR} && chown -R ${NB_USER}:${NB_USER} ${NPM_DIR}
 ---> Using cache
 ---> 8eea23004993
Step 28/46 : USER ${NB_USER}
 ---> Using cache
 ---> f5ae358e09e7
Step 29/46 : RUN npm config --global set prefix ${NPM_DIR}
 ---> Using cache
 ---> d2387e00c958
Step 30/46 : USER root
 ---> Using cache
 ---> 7c155bc59df3
Step 31/46 : RUN bash /tmp/install-miniforge.bash && rm /tmp/install-miniforge.bash /tmp/environment.yml
 ---> Using cache
 ---> 2290af86be94
Step 32/46 : ARG REPO_DIR=${HOME}
 ---> Using cache
 ---> ebe1bab82b02
Step 33/46 : ENV REPO_DIR ${REPO_DIR}
 ---> Using cache
 ---> 7b2321368024
Step 34/46 : WORKDIR ${REPO_DIR}
 ---> Using cache
 ---> e0d3115795cf
Step 35/46 : ENV PATH ${HOME}/.local/bin:${REPO_DIR}/.local/bin:${PATH}
 ---> Using cache
 ---> feb14b2e34a5
Step 36/46 : ENV CONDA_DEFAULT_ENV ${KERNEL_PYTHON_PREFIX}
 ---> Using cache
 ---> ef0969ba9285
Step 37/46 : USER root
 ---> Using cache
 ---> 0ff033f68a02
Step 38/46 : COPY src/ ${REPO_DIR}
 ---> da2cc4199865
Step 39/46 : RUN chown -R ${NB_USER}:${NB_USER} ${REPO_DIR}
 ---> Running in fdb7f3dc0730
Removing intermediate container fdb7f3dc0730
 ---> 2bbcebf63213
Step 40/46 : LABEL repo2docker.ref="768ae83247ec27cf143731211a70ad600c1dd4e4"
 ---> Running in 53285064f64f
Removing intermediate container 53285064f64f
 ---> 4a7cea0057af
Step 41/46 : LABEL repo2docker.repo="https://github.com/JoeyFerment/Diastaticus_genomes"
 ---> Running in da9dc7cf0b81
Removing intermediate container da9dc7cf0b81
 ---> 748b771be0f2
Step 42/46 : LABEL repo2docker.version="0.11.0+98.g8bbced7"
 ---> Running in 7a2640892e3d
Removing intermediate container 7a2640892e3d
 ---> ce403a8fef14
Step 43/46 : USER ${NB_USER}
 ---> Running in 84d5b70c58fe
Removing intermediate container 84d5b70c58fe
 ---> 979a2e3406ad
Step 44/46 : COPY /repo2docker-entrypoint /usr/local/bin/repo2docker-entrypoint
 ---> 18765bee5b75
Step 45/46 : ENTRYPOINT ["/usr/local/bin/repo2docker-entrypoint"]
 ---> Running in 06004ca69210
Removing intermediate container 06004ca69210
 ---> 58b287c4dd5c
Step 46/46 : CMD ["jupyter", "notebook", "--ip", "0.0.0.0"]
 ---> Running in 342815ddfd76
Removing intermediate container 342815ddfd76
 ---> 44c1684d6378
{"aux": {"ID": "sha256:44c1684d637895fd162e8ad8c98f6956a2aae39cba5a83c48643c8e360569e0e"}}Successfully built 44c1684d6378
Successfully tagged gcr.io/binder-prod/r2d-f18835fd-joeyferment-2ddiastaticus-5fgenomes-b4eefb:768ae83247ec27cf143731211a70ad600c1dd4e4
Successfully pushed gcr.io/binder-prod/r2d-f18835fd-joeyferment-2ddiastaticus-5fgenomes-b4eefb:768ae83247ec27cf143731211a70ad600c1dd4e4Built image, launching...
Launching server...
server running at https://hub.gke.mybinder.org/user/joeyferment-diastaticus_genomes-l3fmb3tl/
