
### A Instagram Private Web API client 📷🔥 ❤️

Simple, easy implementation of the Instagram private web API.

## Install

```bash
npm install node-insta-web-api
```

## Usage

```
//get profile data
const Insta = require('node-insta-web-api')
const InstaClient = new Insta();

(async () => {
    await InstaClient.login('username','password');
    const profileData = await InstaClient.getProfileData();
    console.log(profileData)
})()

//get image by username
const Insta = require('node-insta-web-api')
const InstaClient = new Insta();

(async () => {
   await Insta.getCookie()
   const photos = await Insta.getImageByUser('username');
   console.log(photos)
})()

//update bio using existing cookies
const Insta = require('node-insta-web-api')
const InstaClient = new Insta();

(async () => {
    await InstaClient.useExistingCookie()
    const payload = {
        biography: 'test update bio 1'
    }
    const result = await InstaClient.updateProfile(payload)
    console.log(result)
})()
```

## API Reference

* [Instagram](#instagramcredentials-opts)
  * [.useExistingCookie()](#useExistingCookie)
  * [.login(username, password)](#login)
  * [.getProfileData()](#getProfileData)
  * [.changeProfileImage(image)](#changeProfileImage)
  * [.getImageByUser(username)](#getImageByUser)
  * [.getVideoByShortCode(shortCode)](#getVideoByShortCode)

### useExistingCookie()
  ```js
  await client.useExistingCookie()
  ```
  > u can use existing cookies, if you don't want to log in repeatedly

### login(username, password)
  ```js
  await client.login('username', 'password')
  ```
  > Login.
  - `username`: A `String`
  - `password`: A `String`

### getProfileData()
  ```js
    //login required
    await InstaClient.login('username','password');
    const profileData = await InstaClient.getProfileData();
    console.log(profileData)
  ```
  > Getting profile data.

### changeProfileImage(image)
  ```js
    //login required

    //using a url is under development
    //by url
    await InstaClient.login('username','password');
    await InstaClient.changeProfileImage('url')

    //by path
    await InstaClient.login('username','password');
    const photo = path.join(__dirname, 'blackhat.png');
    await InstaClient.changeProfileImage(photo)
  ```
  > Change Profile Image.
  - `image` : A `String` url / image path

### updateProfile(params)
  ```js
    const payload = {
        biography: 'test update bio 1'
    }
    const a = await InstaClient.updateProfile(payload)
    console.log(a)
  ```
  > update profile. for now you can only update your bio.
  - `params`
    - `biography`: A `String` 

### getImageByUser(params)
  ```js
  await client.getImageByUser('username')
  ```
  > Gets user photos.
  - `username`: A `String` 

### getVideoByShortCode(shortCode)
  ```js
    const data = await InstaClient.getVideoByShortCode('CDDs8unBjXX');
    fs.writeFileSync('./test.mp4', data.base64, 'base64')
    console.log(data)
  ```
  > Get video base64 and buffer by short code.
  - `shortCode`: A `String` 


## License

MIT © [Archv Id](https://archv.id/)