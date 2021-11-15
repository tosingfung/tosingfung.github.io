---
tag: [imagej]
layout: post
title: "ImageJ StartupMacro crop, save"
---

- StartupMacro
- Image crop (custom size)
- Get filename and save as TIFF

<!--more-->

[Fiji download](https://imagej.net/Fiji/Downloads)

## StartupMacros

```java
macro "Where to Crop [F5]" {
		run("8-bit");
		//setTool("rectangle");
		makeRectangle(1216, 756, 1600, 1600);
		}
```

```java
macro "Crop Here [F6]" {
		run("Crop");
		//run("Brightness/Contrast...");
		run("Enhance Contrast", "saturated=0.35");
		run("Apply LUT");
		}
```

```java
	macro "save as TIFF and close [F12]"{
		dir = getDirectory("image");
		title = "untitled";
		Dialog.create("File name:");
		Dialog.addString("Input a file name:", title);
		Dialog.show();
		title = Dialog.getString();
		saveAs("Tiff", dir+title);
		close();
	}
```
