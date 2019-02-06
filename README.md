# runtime-abstraction

defines typescript interfaces to abstract from privileged APIs.

Examples:
IFileProvider is an interface that allows multiple implementations for filesystem access and to e.g. read or write files.
The actual implementation can be for Electrons renderer through IPC or as direct fs node module wrapper.
A modules should then be able to either work in the renderer or main process as long as the IFileProvider implementation handles the details of the fs access.

IWindowManager is used to specify the creation and management of webview windows.
A window can then be written with a technology such as Electron, Carlo or even a Webview on Android.
