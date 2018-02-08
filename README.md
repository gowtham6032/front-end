[![Build Status](https://travis-ci.org/microservices-demo/front-end.svg?branch=master)](https://travis-ci.org/microservices-demo/front-end)
[![](https://images.microbadger.com/badges/image/weaveworksdemos/front-end.svg)](http://microbadger.com/images/weaveworksdemos/front-end "Get your own image badge on microbadger.com")


Front-end app
---
Front-end application written in [Node.js](https://nodejs.org/en/) that puts together all of the microservices under [microservices-demo](https://github.com/microservices-demo/microservices-demo).


# Setting up Dev Env

Platform : Ubuntu 16.04

```

# Install Pre reqs
sudo apt-get update  
sudo apt-get install git wget curl build-essential -yq

# Install Nodejs with NPM
cd /tmp
wget -c https://nodejs.org/dist/v4.8.6/node-v4.8.6-linux-x64.tar.xz
sudo tar -xzf node-v4.8.6-linux-x64.tar.xz -C /usr/local --strip-components=1

ln -s /usr/local/bin/node /usr/local/bin/nodejs


# validation  
node --version  
nodejs --version  
npm --version  

# Install Yarn, a package manager for Node

curl -o- -L https://yarnpkg.com/install.sh | bash
export PATH="$HOME/.yarn/bin:$PATH"

# validation
yarn --version

# Clone the source and install using yarn
cd /opt
git clone https://github.com/microservices-demo/front-end.git
cd front-end/
yarn install
```


## Launching the App

The front-end service can be launched with npm using the following command.

export NODE_ENV=production
`npm start`


Service will launch on port **8079**



# Build

## Dependencies

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://docker.com">Docker</a></td>
      <td>>= 1.12</td>
    </tr>
    <tr>
      <td><a href="https://docs.docker.com/compose/">Docker Compose</a></td>
      <td>>= 1.8.0</td>
    </tr>
    <tr>
      <td><a href="gnu.org/s/make">Make</a>&nbsp;(optional)</td>
      <td>>= 4.1</td>
    </tr>
  </tbody>
</table>

## Node

`npm install`

## Docker

`make test-image`

## Docker Compose

`make up`

# Test

**Make sure that the microservices are up & running**

## Unit & Functional tests:

```
make test
```

## End-to-End tests:

To make sure that the test suite is running against the latest (local) version with your changes, you need to manually build
the image, run the container and attach it to the proper Docker networks.
There is a make task that will do all this for you:

```
make dev
```

That will also tail the logs of the container to make debugging easy.
Then you can run the tests with:

```
make e2e
```

# Run

## Node

`npm start`

## Docker

`make server`

# Use

## Node

`curl http://localhost:8081`

## Docker Compose

`curl http://localhost:8080`

# Push

`GROUP=weaveworksdemos COMMIT=test ./scripts/push.sh`
