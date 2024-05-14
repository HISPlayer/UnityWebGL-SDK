# CORS Error

Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.

Error message example:
![Alt text](<cors-error (1).png>)

This error means that the resource that you are trying to load is not allowed to be used from your current origin. In the case of our player SDK, the error usually happens on the stream URL. Therefore, in order to fix this issue, it is needed to configure correctly, on the server/CDN side, the valid origins where your stream URLs are going to be utilized.
