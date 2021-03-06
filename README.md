[![](https://jitpack.io/v/jsramraj/flags.svg)](https://jitpack.io/#jsramraj/flags)

*Android counter part of the [RSFlags](https://github.com/jsramraj/RSFlags) iOS library*

# Lightweight android library for getting flag image for any country
## This entire library is only **175 kb**. Can you believe that?
Simple, no nonsense, lightweight library for getting flag icon for any country from the two character country code


# How this differs from other libraries?
There are plenty of open source libraries available for getting the flag icon. 
But they all include separate image or vector files for each country (there are more than 250 flags in the world) hence become **bulky**.

Unlike all the other libraries, this one includes only **ONE** 
[sprite image](https://github.com/jsramraj/flags/raw/master/flags/src/main/assets/flags_sprite.png)
which consists of all the icons of
all the flags. And the icons are sliced from the sprite image when requested.

### Demo
<img src="./demo/flags-demo.gif" width="40%">

## Usage
### Simple Use
```java
FlagDrawableProvider flagProvider = new Flags.Builder(context)
											 .build();
BitmapDrawable usFlag = flagProvider.forCountry("US")
```
That is all

### Supply your own source image
By default, the flags library uses a 94 kb sprite image with flag icons with size of 32 x 22.

In some cases, this may not be suitable for you. So you can supply your own sprite image with a higher resolution for cases like that.

This is how you supply your source image. Make sure you also give the correct height and width of flag tiles.

```java
FlagDrawableProvider largeFlagProvider = new Flags.Builder(this)
                .setSourceImage(getImageFromAssetsFile(this, "flags_sprite_big.png"))
                .setTileWidth(320)
                .setTileHeight(220)
                .build();
```
To create a sprite image with higher resolution, visit the [Want high res icons?](#Want-high-res-icons?) section

## How to include
### As a dependency
1. Add the JitPack repository to your build file
Add it in your root build.gradle at the end of repositories:
```groovy
allprojects {
	repositories {		
		maven { url 'https://jitpack.io' }
	}
}
```
2. Add the dependency
```groovy
dependencies {
  implementation 'com.github.jsramraj:flags:$version'
}
```
Just replace the *$version* with the appropriate version number, for e.g **v1.0**

### Direct include
If, for some reason, you are not okay with adding a entire library, you can still use this by just adding two files into your project.

* Give this library a star
* Drag the [sprite image](https://github.com/jsramraj/flags/raw/master/flags/src/main/assets/flags_sprite.png) that consists of all the flag icons into your project's asset folder
* Add the [Flags class](https://github.com/jsramraj/flags/blob/master/flags/src/main/java/com/jsramraj/flags/Flags.java) to your project

That is all!!! you are good to go. 

## Want high res icons?
This library is created to occupy very minimum space. So each flag size is only 32x22. If you want a higher resolution image, all you have to do is give a higher resolution image to this library.

You can use my another tool **flag-sprite-creator** to create higher resolution sprite image. 
Find our more about the tool [here](https://github.com/jsramraj/flag-sprite-creator).
The tool is deployed in heroku, you can find it [here](https://flag-sprite-creator.herokuapp.com/)

## License
MIT 
