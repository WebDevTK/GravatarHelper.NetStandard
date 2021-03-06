﻿# Gravatar Helper

A simple [.Net standard library](https://docs.microsoft.com/en-us/dotnet/articles/standard/library) to easily get profile picture, QR code image for profile and profile information for a user from [Gravatar](http://en.gravatar.com/).


## Setup
- Available on Nuget: https://www.nuget.org/packages/GravatarHelper.NetStandard/1.0.0-beta
- To use this library in Xamarin.Forms application, install the [GravatarHelper.NetStandard](https://www.nuget.org/packages/GravatarHelper.NetStandard/1.0.0-beta) nuget package in portable class library and [PCLCrypto](https://www.nuget.org/packages/PCLCrypto/) package in each client project (e.g Android, iOS and UWP).

## Build Status

![App Veyor](https://ci.appveyor.com/api/projects/status/9gwwfn9lb0bxq846?svg=true)
[![MyGet CI](https://img.shields.io/myget/manojkulkarni30/v/GravatarHelper.NetStandard.svg)](http://myget.org/gallery/manojkulkarni30)
[![NuGet](https://img.shields.io/nuget/v/GravatarHelper.NetStandard.svg)](https://www.nuget.org/packages/GravatarHelper.NetStandard/)

## Supported Platform
- .NetFramework 3.5
- .NetFramework 4
- .NetFramework 4.5
- .NetFramework 4.5.1
- .NetFramework 4.5.2
- .NetFramework 4.6
- .NetFramework 4.6.1
- .NetFramework 4.6.2
- .NetStandard 1.3
- Portable Class Library (.NETFramework 4.5, Windows 8.0, WindowsPhone 8.0, WindowsPhoneApp 8.1)- Profile 259

## How To Get Gravatar Image URL ?

To get gravatar image url for email address "[example@test.com](mailto:example@test.com)", use the following syntax in web application.

```html

<!--Returns Gravatar image url over http-->
<img src='@Gravatar.GetGravatarImageUrl("example@test.com")'/>

```
To get image url over https use following syntax
```html

<!--Returns Gravatar image url over https-->
<img src='@Gravatar.GetSecureGravatarImageUrl("example@test.com")'/>

```
There are different overload methods available where you can specify different parameters like image size, file extension, rating, gravatar default image type etc. 

## How To Get the QR Code Image For Gravatar Profile ?

To get the QR code image for email address "[example@test.com](mailto:example@test.com)", use the following syntax in web application

```html

<img src='@Gravatar.GetGravatarProfileQrCodeImage("example@test.com")'/>

```

## How To Get The Gravatar Profile Information ?

To get the gravatar profile information for a user using email address "[example@test.com](mailto:example@test.com)", use the following syntax.

```csharp

// Available only for .Net Framework 4.5 and above
await Gravatar.GetGravatarProfileInformationAsync("example@test.com");

// For .Net Framework 3.5 and 4.0
GetGravatarProfileInformation("example@test.com");

```
Above method will return an object of type ```OperationResult```. 

```csharp

    public class OperationResult
    {
        public bool Success { get; set; }

        public ProfileInformation Profile { get; set; }

        public string Error { get; set; }
    }

```
If request for profile information is successful, then ```Success``` property will be set to true and ```Profile``` object will contain the profile information.

If request for profile information failed, then ```Success``` property will be set to false, ```Profile``` object will be ```null``` and ```Error``` property will contain the error message.

**Note: Profile requests will only resolve for the primary email address**

## License

[Apache 2.0](https://github.com/manojkulkarni30/GravatarHelper.NetStandard/blob/master/License.txt)