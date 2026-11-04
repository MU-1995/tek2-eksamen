```bash
ssh -i ~/downloads/tek-eks-vm_key.pem azureuser@20.91.143.54
```

# /openssl - symmetrisk kryptering/
echo "hemmelig besked" > hemmelig.txt

```bash
openssl enc -aes-256-cbc -salt -pbkdf2 -in hemmelig.txt -out hemmelig.enc
```
cat hemmelig.enc

```bash
openssl enc -aes-256-cbc -d -pbkdf2 -in hemmelig.enc -out dekrypteret.txt
```
cat dekrypteret.txt

# /GPG/
gpg --full-generate-key
# Vælg: 1, 2048, 0, y, Gpg, gpg@gpg.com, O, gpg, Take this one anyway

echo "hemmelig besked" > besked.txt

gpg --encrypt --armor -r "Gpg" besked.txt

cat besked.txt.asc

gpg --decrypt besked.txt.asc
# /SSH-nøglepar/
ssh-keygen -t ed25519

ls ~/.ssh/

cat ~/.ssh/id_ed25519.pub

cat ~/.ssh/id_ed25519

ls -la ~/.ssh/
# /Certifikate/
openssl s_client -connect ek.dk:443
# /WireShark - TLS handshake/
ip.addr == 195.254.168.52
# /SSH tunnel/
ssh -i ~/downloads/tek-eks-vm_key.pem -L 8080:localhost:80 azureuser@20.91.143.54

sudo python3 -m http.server 80

http://localhost:8080
# /WireGuard/
