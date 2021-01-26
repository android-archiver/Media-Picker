[![Webp-net-resizeimage-26.jpg](https://i.postimg.cc/prsfWNCD/Webp-net-resizeimage-26.jpg)](https://postimg.cc/LgZYDbrX)
[![16113251508601.jpg](https://i.postimg.cc/2yjZh36s/16113251508601.jpg)](https://postimg.cc/hzwvqDVs)

# Media-Picker

Android Library for easing Media Selection to your apps with support for Images and Videos with a beautiful sample app.

## Features

* Written in Kotlin
* Pick Multiple Images and Videos
* Restrict User to Pick no of Images and Videos
* Capture Images and Videos
* Latest CameraX API

## Gradle Dependency

* Add the JitPack repository to your project's build.gradle file

```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

* Add the dependency in your app's build.gradle file

```
dependencies {
    implementation 'com.github.akshaaatt:Media-Picker:1.0.0'
}
```

## Usage

#### Initialization

```kotlin
 val dazzleOptions =
            DazzleOptions.init().apply {
                maxCount = 5                        //maximum number of images/videos to be picked
                maxVideoDuration = 10               //maximum duration for video capture in seconds
                allowFrontCamera = true             //allow front camera use
                excludeVideos = false               //exclude or include video functionalities
            }

        binding.selectMedia.setOnClickListener {
            Dazzle.startPicker(this, dazzleOptions)    //this -> context of Activity or Fragment
        }
```

#### Callback

```kotlin
  override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)

        if (resultCode == Activity.RESULT_OK && requestCode == REQUEST_CODE_PICKER){
            val mImageList = data?.getStringArrayListExtra(PICKED_MEDIA_LIST) as ArrayList //List of selected/captured images/videos
            mImageList.map {
                Log.e(TAG, "onActivityResult: $it" )
            }
        }
    }
```

## Contribution

You are most welcome to contribute to this project!