# Concourse resources website (CI/CD Pipeline enabled)

Any change pushed into the repositories (including the submodule) would trigger the pipeline.

- Website link: https://intense-wave-04461.herouapp.com 
- Project link: https://dev.azure.com/anmolvirdi/concourse-resources
- Pipeline link: https://dev.azure.com/anmolvirdi/concourse-resources/_build 

# About the project (Concourse resource website):

## Architecture:

- The code is mainly a Golang back-end with an elm front-end.
- We also rely on the `resource-types` directory as the persistence of the website.

## Run Locally:

There are multiple ways to run the code locally:

- to run directly from the code, you can run the following commands:

  - if you want to use a different port, the app uses the environment variable `PORT` to select its port or else it will use port `9090`.

  ```bash
  cd warehouse/web
  yarn install && yarn build
  cd ..
  go run ./main.go
  ```

- To run using docker:

  ```bash
  docker build -t dutyfree
  docker run dutyfree -p 9090:9090
  ```

- To run using docker compose: `docker-compose up --build` that will build the image locally and run the website on port `9090`.

### Notes:

- We are also working on a helm chart to deploy the website which is currently very opinionated towards objects that exist in the k8s version of GKE.
- Using the previous commands you will be able to access the application through: `http://localhost:9090`.
- To use a different set of resource types, you can change the resource types under the directory `resource-types`, this would allow running different versions of the website.

## Tests:

- To test the back-end server:

  ```bash
  cd warehouse
  
  go get -u github.com/onsi/ginkgo/ginkgo
  
  ginkgo -r -keepGoing .
  ```

- To test the front-end code: `cd warehouse && yarn install && yarn test`.
