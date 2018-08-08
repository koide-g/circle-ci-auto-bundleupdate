# CircleCI bundle update

[![CircleCI](https://circleci.com/gh/koide-g/circle-ci-auto-bundleupdate/tree/develop.svg?style=svg)](https://circleci.com/gh/koide-g/circle-ci-auto-bundleupdate/tree/develop)


trigger with cron schedule

```
workflows:
  version: 2
  build:
    jobs:
      - build
  bundleupdate:
    jobs:
      -ci-bundle-update
    triggers:
      - schedule:
          cron: "0,15,30 * * * 1-5"  # debug
          # cron: "0 22 * * 0"  # 日曜日 UTC 22:00 に実行
          filters:
            branches:
              only:
                - develop # developだけで実行
```

trigger only pushing develop branch

```
workflows:
  version: 2
  build:
    jobs:
      - build
  bundleupdate:
    jobs:
      - ci-bundle-update:
          filters:
            branches:
              only:
                - develop
```