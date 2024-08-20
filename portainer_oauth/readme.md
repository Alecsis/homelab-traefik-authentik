#If you had a portainer instance like me, you can make a backup and restore in the new container!

https://www.youtube.com/watch?v=cx7iovpxtSw&pp=ygUccG9ydGFpbmVyIGJhY2t1cCBhbmQgcmVzdG9yZQ%3D%3D


With Oauth you dont need this line 
```
      - "traefik.http.routers.traefik-dashboard.middlewares=authentik@file"
```

In Authentik go to providers and copy the Client ID and Secret.

Then go to services and link it to the name you gave to providers,
and fill in the domain name you gave to portainer.


You can use the offical docs for more info!
https://docs.goauthentik.io/integrations/services/portainer/


After you do that you can sign into it with OAuth!
You should see a new button to sign into oauth, and it will force you to sign it via Authentik.


Now with this login it creates a new user based on your Authentik email/user and you will need to SIGN out and go back into your main admin account to give the new one 
admin perms!
