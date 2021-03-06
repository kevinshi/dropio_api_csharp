drop.io API library for C#
============================

Before using the Dropio library, the application must set an API key.  This key will be used for all requests to the server.  To get an API key, go to [http://api.drop.io/](http://api.drop.io/).  Then make sure you set the API key before you use the API:

    ServiceProxy.Instance.ServiceAdapter.ApiKey = "e27079f977e83facedcba464b7580d2a0318131b";

The Drop object
---------------

There are two ways to get a `Drop` object.  The first is to access an existing drop:

    Drop drop = Drop.find("mystuff");
    Drop auth_drop = Drop.find("mystuff", "b9b2c8f2b8e655679d2fb62b83f8efec4fb4c8af")

`Drop#find` takes two arguments: the name of the drop to get, and a credential token.  This can be an admin token, a user token, an admin password, or a guest password.  The drop's capabilities will be limited by the token, and the token is optional.  If the drop is authenticated with the admin token, it will be able to do anything.  If the drop is not authenticated with a token, it will have the same capabilities as any user visiting the drop.  If the drop is not found or the token is not accepted, `#find` will return `null`.

