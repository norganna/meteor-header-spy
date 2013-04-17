meteor-header-spy
=================

A drop in javascript file which hooks into the request object.

It saves client request headers and ip addresses against the sockjs session id so that you may retrieve them later in the meteor request.

## Installation:

Drop the header-spy.js into your meteor app's server directory.

## Usage:

### get_http_header(client, header);

Returns the value of the given header.

 * *client*: The meteor client object (usually `this` from within publish functions.
 * *header*: String containing the name of the header to retrieve.

### get_http_remote_ip(client, direct);

Returns the derived IP address of the client based on remote socket address and http-forwarded-for headers.

 * *client*: The meteor client object (usually `this` from within publish functions.
 * *direct*: Boolean, if true, does not use http-forwarded-for header, instead just returns the socket ip address. This is usually wrong if you have some kind of proxy in front of meteor.
    
## Example:

    Meteor.publish('test_subscription', function() {
      var language = get_http_header(this, 'ACCEPT_LANGUAGE'),
          client = get_http_remote_ip(this);
      console.log('Client', client, 'requested language preference', language);
    });

## License:

Project code is released under CC0 license:

<a rel="license" href="http://creativecommons.org/publicdomain/zero/1.0/">
<img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
</a>
    
  
