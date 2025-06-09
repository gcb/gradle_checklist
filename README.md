# gradle checklist

Shipping random files in the code repo, like java builds weren't bad and finick enough! 


- [ ] delete `gradlew` and `gradlew.bat` (know knows where it came from or how old they are)
- [ ] delete `gradle/wrapper/gradle-wrapper.jar` (it's probably a (old) trojan)
- [ ]  make sure `gradle.properties` is empty or all commented out.
- [ ]  see `build.gradle` template bellow.
- [ ]  see `gradle/wrapper/gradle-wrapper.properties` template bellow.\
- [ ]  now run `gradle` from your distro on the project root.


## Templates

### `build.gradle`

See: [canonical source]()
```
buildscript {
    repositories {
        jcenter()
        // google() // Uncomment if using google owned libraries
    }
    dependencies {
        // see https://developer.android.com/build/releases/gradle-plugin
        // note their release notes are assinine. they write "8.5" when they mean "8.5.0"
        //classpath 'com.android.tools.build:gradle:8.5.0' // min gradle 8.7 + java17
        // uncomment above line if android build. Also uncomment the other two google() lines.

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
allprojects {
    repositories {
        jcenter()
        // google() // Uncomment if using google owned libraries
    }
}
task clean(type: Delete) {
    delete rootProject.buildDir
}
```

### `gradle/wrapper/gradle-wrapper.properties`

```
# get verions to use on the last line at https://gradle.org/releases/
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-8.10-bin.zip
```
