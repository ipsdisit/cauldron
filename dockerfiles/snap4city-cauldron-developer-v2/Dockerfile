FROM disitlab/snap4city-nodered-v2.2.2-adv:v10

# permissions
USER root
RUN chmod a+w /usr/src/node-red
RUN chown -R "$USER" /usr/src/node-red

# base for building cauldron
RUN npm install -g node-gyp

# Install additional packages from github
WORKDIR /usr/src
RUN git clone -b snap4city-cauldron-v2 https://github.com/ipsdisit/cauldron

# Build cauldron
WORKDIR /usr/src/cauldron
RUN npm install
RUN npm run build
WORKDIR /usr/src

#copy modules
# RUN cp -r cauldron/. /usr/src/node-red/
RUN cp -r cauldron/packages/node_modules/@node-red /usr/src/node-red/node_modules/
#RUN cp -r cauldron/node_modules/node-watch /usr/src/node-red/node_modules/
#RUN cp -r snap4city/nodered-snap4city-microservices/snap4city-user-authentication /usr/src/node-red/node_modules/
#RUN cp -r node-red-contrib-snap4city-user /usr/src/node-red/node_modules/
#RUN cp -r node-red-contrib-snap4city-developer /usr/src/node-red/node_modules/
#RUN cp -r node-red-contrib-snap4city-d3-dashboard-widgets /usr/src/node-red/node_modules/

USER node-red
WORKDIR /usr/src/node-red
