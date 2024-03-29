# Good habits when starting JS Projects

## Linting

```
$ npm install eslint -g
$ eslint --init

```

## CI/CD

### CircleCI Example CI testing config (.circleci/config.yml)
```
version: 2
jobs:
  build:
    working_directory: ~/mern-starter
    # The primary container is an instance of the first image listed. The job's commands run in this container.
    docker:
      - image: circleci/node:4.8.2-jessie
    steps:
      - checkout
      - run:
          name: Update npm
          command: 'sudo npm install -g npm@latest'
      - restore_cache:
          key: dependency-cache-{{ checksum "package.json" }}
      - run:
          name: Install npm wee
          command: npm install
      - save_cache:
          key: dependency-cache-{{ checksum "package.json" }}
          paths:
            - node_modules
  test:
    docker:
      - image: circleci/node:4.8.2-jessie
    steps:
      - checkout
      - run:
          name: Test
          command: npm test
      - store_artifacts:
          path: test-results.xml
          prefix: tests

workflows:
  version: 2
  build_and_test:
    jobs:
      - build
      - test:
          requires:
            - build
```

## Creating a new React app using TypeScript
```
$ yarn create react-app app --typescript
```

## Installing storybook into js project (for testing components)
```
$ npx -p @storybook/cli sb init --type react
```

## For JS Apps

### Ant Design https://ant.design/docs/react/introduce
```
$ yarn add antd
```
