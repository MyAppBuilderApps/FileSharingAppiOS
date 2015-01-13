**Apache Cordova File Sharing App iOS Application**

MyAppBuilder File Sharing App is a cloud based file sharing platform.

**Versions and Tags**

Sample app is built and tested with Cordova 3.5.0 iOS and we only support Cordova version greater than 3.0.

**Required reading**

Please see the Getting Started With iOS for PhoneGap guide [here](http://docs.phonegap.com/en/3.5.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide).

File Sharing App show user files in list that functions like a UITableView and also user can upload files via mobile.Tap tableview button user can share file,Delete file,Rename file,Export file(Download file,Email file)

### 1) **_App Controller_**  ##########

 1) www folder

i) index.html

ii) js/index.js

iii) js/controller.js

## 2)**_Sign up_** ##########

Register controller inside the index.js

API For User Sign Up: **http://build.myappbuilder.com/api/users.json**

Code:

$http({method: "POST", url: 'http://build.myappbuilder.com/api/users.json', cache:false, params:{"name":$scope.userDetail.fullname,"username":$scope.userDetail.username,"email":$scope.userDetail.email,"password":$scope.userDetail.password,"password_confirmation":$scope.userDetail.passwordConfirm}})

.success(function(data,status,headers,config){

})

.error(function(data,status,headers,config){

})

## 3)**_Sign in_** #############

Login controller inside the index.js

API For User Sign In: **http://build.myappbuilder.com/api/login.json**

Code:

var formData = new FormData();

formData.append("login",$scope.userlogin.userid); // Username

formData.append("password",$scope.userlogin.password); // Password

$http.post('http://build.myappbuilder.com/api/login.json', formData,{

                transformRequest: angular.identity,

                headers: {'Content-Type': undefined}

})

.success(function(data,status,headers,config){

})

.error(function(data,status,headers,config){

})

### 4)**_Files Retrieve data from MAB server_** #####

API For User retrive files: **http://build.myappbuilder.com/api/files.json**

Count = 20 //_This integer refer how many data retrieve from myappbuilder._

Maximum count = 200

Minimum count = 20 

code:

$http({method:'GET', url:'http://build.myappbuilder.com/api/files.json', cache:false, params:{'api_key':loginStorage.api_key,'count':'','page':'','folder_id':''}})

.success(function(data, status, headers, config){

})

.error(function(data,status,headers,config){

})

**** 5)**File Upload to MAB *******************

API For User Upload Files: **http://build.myappbuilder.com/api/files/new.json**

code:

var formData = new FormData();

formData.append("api_key",loginStorage.api_key);

formData.append("file", $('#newrootfiles').get(0).files[0]);

$http.post('http://build.myappbuilder.com/api/files/new.json',formData,{

     transformRequest: angular.identity,

     headers: {'Content-Type': undefined}

})

.success(function(data, status, headers, config){

})

.error(function(data,status,headers,config){

})

****** **Folder Creation** ******************

API For User Folder Creation: **http://build.myappbuilder.com/api/folders.json**

code:

var formData = new FormData();

formData.append("api_key",loginStorage.api_key);

formData.append("name",$scope.folder.name);

$http.post('http://build.myappbuilder.com/api/folders.json', formData,{

     transformRequest: angular.identity,

     headers: {'Content-Type': undefined}

})

 .success(function(data,status,headers,config){

})

.error(function(data,status,headers,config){

})

****** **Deleting File** ********************

API For User Upload Files: **http://build.myappbuilder.com/api/folders/destroy.json**

item.id // Folder id or file id

code:

$http({method:"DELETE", url:'http://build.myappbuilder.com/api/folders/destroy.json', cache:false, params:{'api_key':loginStorage.api_key, 'id':item.id}})

.success(function(data,status,headers,config){

})

.error(function(data,status,headers,config){

})

******* **MAB Rename file** ***************

API For User Rename Files: **http://build.myappbuilder.com/api/files/rename.json**

folder.editId // Folder id or file id

folder.editname // Folder name or file name

code:

$http({method:'PUT', url:'http://build.myappbuilder.com/api/files/rename.json', cache:false, params:{'api_key':loginStorage.api_key, 'id':$scope.folder.editId, 'name':$scope.folder.editname}})

.success(function(data,status,headers,config){

})

.error(function(data,status,headers,config){

})

******* **MAB share file** ***************

i) FaceBook API

ii) Twitter API

iii) Email Plugin

#### **_6)FrameWork_** ###########

1)IonicFramework

2)Phonegap

3)Cordova

4)MessageUI