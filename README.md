# Mp4parser

Applies [this PR](https://github.com/sannies/mp4parser/pull/471) to the
[mp4parser](https://github.com/sannies/mp4parser) codebase and publishes the
build artifacts.

## Usage

```
dependencies {
    implementation 'org.mp4parser:isoparser:9.9.0-SNAPSHOT'
    implementation 'org.mp4parser:muxer:9.9.0-SNAPSHOT'
}
```

```
repositories {
    maven {
        url = "https://github.com/mark-sentigrate/mp4parser/blob/master/.m2/repository"

        content {
            includeGroup("org.mp4parser")
        }
    }

    // Other repositories
}
```

## Building

```bash
docker run --rm \
  -u $(id -u):$(id -g) \
  -v "$PWD:/usr/src/mymaven" \
  -v "$PWD/.m2:/var/maven/.m2" \
  -e MAVEN_CONFIG=/var/maven/.m2 \
  -w /usr/src/mymaven \
  maven:3.8.7-openjdk-18-slim mvn -Duser.home=/var/maven clean deploy
```

After this, commit & push to make the new version available.
