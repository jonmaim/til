# Android development

## Migrating project to AndroidX

1) Add `gradle.properties` file at the root of the poject containing:

```
android.useAndroidX=true
android.enableJetifier=true
```
2) Support librairies like `android.support.v4.app.ActivityCompat` are replaced by there AndroidX compatible ones: 
`androidx.core.app.ActivityCompat`, etc. So building project will fail and each support class needs to be adapted. 

Here is the [mapping](https://gist.github.com/jonmaim/891ab2d160aaf24353b7a1a1768fd689) and [original project](https://github.com/dpa99c/cordova-plugin-androidx-adapter).
