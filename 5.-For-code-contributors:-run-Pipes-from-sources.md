# Prepare the environment

Prerequisites:
Gradle >= 4.6
npm



Do the following:

- Clone the repo
- Run `npm install`
- Do following:

`cd java-middle tier`

run `gradle wrapper`

`cp node_modules_override/litegraph.js node_modules/litegraph.js/build/litegraph.js`

# Run the UI locally

`gradle dev`

# Build the jar

Run `buildPackageUiJar.sh` script which will build the Pipes Jar. It can be found in ./java-middle-tier/build/libs
