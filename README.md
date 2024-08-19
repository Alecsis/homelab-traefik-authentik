##Traefik Proxy 

This service was made to give my services an domain and not give those "Site Not Secure" warnings on chrome.

Anyways you would need docker and a cloudflare domain.

First step is to set up an A record pointing to your PRIVATE IP that includes your whole domain
![image](https://github.com/user-attachments/assets/330e2ecc-ad1d-4082-81cf-10b9b7e2aa06)

Then set SSL/TLS encryption mode to Full this would resolve any conflicts later on.

Then Fill in your CF account details on the compose enviroment varables.

Looking at the label headers
```
      - "traefik.enable=true"
      - "traefik.http.routers.traefik-dashboard.rule=Host(`proxy.yourdomain.tech`)"
      - "traefik.http.routers.traefik-dashboard.entrypoints=websecure"
      - "traefik.http.routers.traefik-dashboard.tls=true"
      - "traefik.http.routers.traefik-dashboard.tls.certresolver=letsencrypt"
```
```
"traefik.enable=true"
```
Turns tells the container to use traefik
```
"traefik.http.routers.traefik-dashboard.rule=Host(`proxy.yourdomain.tech`)"
```
The Domain where the service will be located at
```
"traefik.http.routers.traefik-dashboard.entrypoints=websecure"
```
Route the service throught traefik's 443 port.
```
"traefik.http.routers.traefik-dashboard.tls=true"
"traefik.http.routers.traefik-dashboard.tls.certresolver=letsencrypt"
```
Both are params needed to use 443 (HTTPS)


#AAAAnD if everything works you should see this!

![image](https://github.com/user-attachments/assets/1933a2ed-f452-4e22-b450-4bb8e4a7298d)

