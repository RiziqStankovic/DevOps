Untuk Autentikasi supaya prometheus lebih aman saya akan gunakan `apache2-utils`

```
sudo apt install apache2-utils
```

![image](https://user-images.githubusercontent.com/106061407/176593069-708df5b7-050b-4338-aed5-25d2260079ed.png)

Kemudian generate password dengan htpasswd

```
sudo htpasswd -c /etc/nginx/.htpasswd <username>
```

![image](https://user-images.githubusercontent.com/106061407/176593296-ba966fc0-dc18-4099-8a58-4a8c8dfd2bf9.png)


Kemudian masuk ke konfigurasi `prometheus.conf` `/etc/nginx/housy`

```
sudo nano /etc/nginx/housy/prometheus.conf 
```

Tambahkan konfigurasi berikut

```
location / {
          auth_basic "prometheus";
          auth_basic_user_file /etc/nginx.htpasswd;


        }
```

![image](https://user-images.githubusercontent.com/118950953/232962135-3a761003-558c-4383-bebd-4d0a22be3a2d.png)

![image](https://user-images.githubusercontent.com/106061407/176593749-e6f76dd1-8428-401b-a336-c51c485038ce.png)


save dan exit 

Kemudian cek syntax dengan menggunakan `sudo nginx -t`

![image](https://user-images.githubusercontent.com/106061407/176594502-7747ac24-b5fd-43bf-acc0-d60c2a4f3a35.png)


Kemudian restart systemctl nginx

```
sudo systemctl restart nginx.service 
```

![image](https://user-images.githubusercontent.com/106061407/176594598-1147da26-e3d0-4446-b9de-ecb4e32a1cbb.png)

Dan berikut hasilnya

![image](https://user-images.githubusercontent.com/106061407/176594618-fd1e9c17-a274-470e-bb13-a714d89d5320.png)
