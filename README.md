# AWS Amplify DataStore Demo

## Instructions

0. Install the CLI tools.
```
yarn global add create-react-app
yarn global add @aws-amplify/cli
yarn global add amplify-app
```

1. Setup new React project.
```
create-react-app amplify-datastore-app
code amplify-datastore-app
yarn start

git init
git add -A
git commit -a -m 'Setup new React project.'

# Open http://localhost:3000
```

2. Add Amplify DataStore to the project.
```
amplify-app
yarn add @aws-amplify/core @aws-amplify/datastore

git add -A
git commit -a -m 'Add Amplify DataStore to the project.'
```

3. Add GraphQL schema and then generate the model(s).
```
curl -o amplify/backend/api/amplifyDatasource/schema.graphql \
  https://raw.githubusercontent.com/aonz/amplify-datastore-demo/master/schema.graphql

yarn amplify-modelgen

git add -A
git commit -a -m 'Add GraphQL schema and then generate the model(s).'
```

4. Use Amplify DataStore in the local mode.
```
curl -o src/App.js \
  https://raw.githubusercontent.com/aonz/amplify-datastore-demo/master/App.js

git add -A
git commit -a -m 'Use Amplify DataStore in the local mode.'

# Test the local version.
```

5. Deploy the backend on AWS.
```
# Uncomment 2 lines below in src/App.js
# import awsConfig from "./aws-exports";
# Amplify.configure(awsConfig);

yarn amplify-push
# About 5 mins

git add -A
git commit -a -m 'Deploy the backend on AWS.'

# Test the version with the backend on AWS.
```

6. Deploy the frontend on AWS.
```
aws codecommit create-repository --repository-name AmplifyDataStoreDemo \
  --repository-description 'AWS Amplify DataStore Demo'
git remote add origin ssh://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/AmplifyDataStoreDemo
git push --set-upstream origin master

amplify add hosting
# Choose `Hosting with Amplify Console` and then `Continuous deployment`

git add -A
git commit -a -m 'Deploy the frontend on AWS.'

# Test the version with both the frontend and backend on AWS.
```

7. Cleanup
```
amplify delete
aws codecommit delete-repository --repository-name AmplifyDataStoreDemo
```

## Reference
https://github.com/sebsto/amplify-datastore-js-e2e