##Run your app in production
### Configure containers
#### Start containers automatically

Sử dụng cờ `--restart` :

* `no` : Do not automatically restart the container. (the default)
* `on-failure` : Restart the container if it exits due to an error, which manifests as a non-zero exit code.
* `unless-stopped` : Restart the container unless it is explicitly stopped or Docker itself is stopped or restarted.
* `always` : Luôn luôn restart lại container khi nó dừng.

Ví dụ: `$ docker run -dit --restart unless-stopped redis`

Ghi nhớ những điều sau : 




#### Tài liệu: 

https://docs.docker.com/config/containers/start-containers-automatically/

