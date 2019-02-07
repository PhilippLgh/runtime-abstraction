# Project "Runtime Abstraction"

## Motivation

Frameworks and runtime technologies like Electron, Carlo, Cordova, NW.js, Tau or PWAs try to provide traditional Web Apps with extra APIs and "super powers" that close the gap between native and hybrid Web applications.

Unfortunately, these extra APIs are non-standard, very vendor specific, can change frequently, and create lock-in effects.

If an application is written e.g. for Electron it can run cross platform on Desktop PCs but will need to be refactored and changed to communicate with APIs from e.g. Cordova to run on mobile.

## Goal

The goal of this project is to define a common subset of APIs (typescript interfaces) that can be implemented "cross-runtime-technology".
If an application is using an implementation of such an interface it is guaranteed to run without any changes on multiple platforms.

Some of these privileged APIs will require permissions and user interaction and should therefore be defined and used in a way that they are asynchronous and can fail.

## Examples

### IFileProvider
IFileProvider is an interface that allows multiple implementations for filesystem access and to e.g. read or write files.
The actual implementation can be for Electron's renderer through IPC or as direct fs node module wrapper on the main process.
A modules should then be able to either work in the renderer or main process as long as the IFileProvider implementation handles the details around the fs access.

### IWindowManager
IWindowManager is used to specify the creation and management of webview windows / renderer surfaces.
A renderer can then be a BrowserWindow in Electron, a Chrome Browser in Carlo or an Activity with a Webview on Android.


## Getting Started & Getting Involved

1. Provide an implementation for a platform named "runtime-abstraction-x" e.g. [runtime-abstraction-electron](https://github.com/PhilippLgh/runtime-abstraction-electron).

2. Use issues on this repository for API discussions and coordination.