---
title: Typora Image with GitHub repo
layout: post
tag: software
---

- Set up GitHub repo for image storage
- Image upload with PicGo core in Typora

## GItHub image repository

![image-20211117160301378](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117160301378.png)

#### Create a GitHub repository with the name `images`. It must be a Public repo to work with PicGo. Uncheck all three boxes.

![image-20211117160647256](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117160647256.png)

#### Open GitHub account setting in the upper right (not repo setting).

![image-20211117160933715](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117160933715.png)

#### Go to Developer settings

![image-20211117161144339](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117161144339.png)

#### Click on Personal access tokens

![image-20211117161431704](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117161431704.png)

#### Click generate new token. Give a name (such as typora-image-upload). Set No expiration. In the scopes, only check repo. Click Generate token. In the next page, copy the personal token.

## PicGo core in Typora

![image-20211117104050957](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117104050957.png)

#### Open Typora / File / Preference / Image. When Insert...No special action. Check/uncheck the boxes as above.

![image-20211117104546372](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117104546372.png)

#### Image uploader choose PicGo-Core (command line). Click Download or Upgrade and wait for PicGo download and installation. Then click Open Config File and paste the following and save the json file.

```json
{
  "picBed": {
    "uploader": "github",
    "github": {
      "repo": "tosingfung/images",
      "token": "xxxxxx",
      "branch": "master"
    }
  },
  "picgoPlugins": {}
}
```

![image-20211117162120088](https://raw.githubusercontent.com/tosingfung/images/master/image-20211117162120088.png)

#### You can now press the Test Uploader. This will attampt to upload two typora icon images to the GitHub repo.
