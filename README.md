# certbot

certbot yüklemek için öncelikle sistem update ve upgrade yapalım

```
apt-get update && apt-get upgrade -y
```

daha sonra gerekli uygulamaları yükleyelim.

```
apt-get install certbot
apt-get install openssl
```

yükledikten sonra yapacağımız tek şey DNS challange başlatarak sertifika almak

```
sudo certbot certonly --manual --preferred-challenges=dns --email <your-mail-adress>  --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d example.com -d *.example.com
```

bundan sonra size her domain için bir TXT record verecek bunu DNS lerinizi yönettiğiniz yerde tanımlamanız gerek.

certifikayı aldıktan sonra pfx olarak kullanmak için.

```
openssl pkcs12 -export -in full.pem -inkey privateky.key -out output.pfx
```

certificate check


````
openssl x509 -in server.crt -text -noout
