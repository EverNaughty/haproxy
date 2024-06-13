# Generate a unique private key (KEY)
> openssl genrsa -out mydomain.key 2048

# Generating a Certificate Signing Request (CSR)
> openssl req -new -key mydomain.key -out mydomain.csr

# Creating a Self-Signed Certificate (CRT)
> openssl x509 -req -days 365 -in mydomain.csr -signkey mydomain.key -out mydomain.crt

# Append KEY and CRT to mydomain.pem
> bash -c 'cat mydomain.key mydomain.crt >> /etc/ssl/private/mydomain.pem'

# Specify PEM in haproxy config
> nano /etc/haproxy/haproxy.cfg

# Add this line on HA PROXY CONF :
> bind *:443 ssl crt /etc/ssl/private/mydomain.pem
