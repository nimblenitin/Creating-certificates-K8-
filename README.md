# Creating-certificates-K8

Client authentication can be setup with certificates manually through easyrsa.

Simple example-

*As Root*
```

1. Download the patched version of easyrsa3 
$ curl -LO https://storage.googleapis.com/kubernetes-release/easy-rsa/easy-rsa.tar.gz

2. Unpack the patched version of easyrsa3
$ tar xzf easy-rsa.tar.gz

3. Initialize the patched version of easyrsa3
$ cd easy-rsa-master/easyrsa3 5. 
$ ./easyrsa init-pki

4. Generate a new certificate authority (CA). --batch sets automatic mode; --req-cn specifies the Common Name (CN) for the CA's new root certificate.
$ ./easyrsa --batch "--req-cn=${MASTER_IP}@`date +%s`" build-ca nopass\

5. The below can be used to distribute a self-signed CA certificate to all clients and refresh the local list for valid certificates. 
$ sudo cp /root/cert/easy-rsa-master/easyrsa3/pki/private/ca.key \
$ /usr/local/share/ca-certificates/kubernetes.crt
$ sudo update-ca-certificates

```
*As Root*



