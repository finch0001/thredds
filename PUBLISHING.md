# Publishing feature/s3+hdfs branch

Ensure the build version is updated in build.gradle so that the commit hash matches the hash of the code you're building. The version format should be `feature-s3+hdfs-<hash>`.

Run: `./gradlew assemble`

Then publish:

```bash
aws --profile geotrellis s3 cp \
  ./cdm/build/libs/cdm-feature-s3+hdfs-<hash>.jar \
  s3://geotrellis-build-artifacts/thredds \
  --acl public-read
```

To use this project in SBT, add the following line to your library dependencies:

```
"edu.ucar" % "cdm" % "feature-s3+hdfs-<hash>" from "https://geotrellis-build-artifacts.s3.amazonaws.com/thredds/cdm-feature-s3%2Bhdfs-<hash>.jar"
```
