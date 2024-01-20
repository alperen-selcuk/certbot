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
openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out output.pfx
```

certificate check


```
openssl x509 -in <certificate> -text -noout
```


örnek websitesinde port 8080 olarak değiştireceğiz

```
apt-get install apache2

vi /etc/apache2/port.conf 
```

