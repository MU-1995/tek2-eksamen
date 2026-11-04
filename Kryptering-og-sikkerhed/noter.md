Eksaempler på spørgsmål om kryptering:
# 1. Hvad er forskellen på symmetrisk og asymmestisk kryptering, og hvornår bruger man hvad?
symmestrisk kryptering burger én nøgle til kryptering og dekryptering.
Hurtigt, men usikkert

assymetrisk kryptering bruger et nøglepar. public key og private key. public key krypterer og private key dekrypterer.
langsommere, men sikkert ved nøgleudveksling - public key kan deles frit.

gpg er asymmetrisk, openssl er symmetrisk. Adgang til vm er asymmetrisk
# 2. Hvad er en hash-funktion, og hvordan adskiller den sig fra kryptering?
en hash funktion er et fingeraftryk. tager et vilkårligt input og giver fast output.

hash er envejs og kan ikke dekrypteres - samme input giver altid samme hash.

hash formål : verifikation - adgangskoder, git-commits

kryp formål : fortrolighed - TLS, SSH
# 3. Hvad er en digital signatur, og hvad kan man bruge den til?
Afsenderen krypterer beskeden med sin private key — det er signaturen. Kun afsenderen kan gøre det fordi kun afsenderen har den private key.

Modtageren dekrypterer med afsenderens public key. Hvis det virker, ved modtageren at beskeden kom fra afsenderen — fordi kun afsenderen har den private key der passer til den public key.

fx. TLS-certifikater
# 4. Hvad er GPG, og hvad kan man bruge det til?
GPG står for GNU Privacy Guard.

et værktøj til asymmestrisk kryptering og digitale signaturer.
# 5. Hvordan forgår et TLS handshake? (ClientHello, ServerHello, certifikat, nøgleudveksling)
client hello og server hello - udveksler nøgler, og så bliver de enige om at bruge symmestrisk kryptering.
# 6. Hvad er en certifikatkæde, og hvad er en Certificate Authority(CA)?
min computer siger "jeg vil gerne ind på ek.dk" let's encrypt siger: "hey ek.dk bevis at du virkelig er ek.dk” ek.dk beviser det let's encrypt siger "ok tak for bevis" dem der er over lets encrypt som hedder noget med iir eller et eller andet jeg aldrig kan huske siger "cool vi stoler på lets encrypt" og min computer siger "tak nu har jeg trygt adgang"

En CA er en organisation der står for at sikre at hjemmesider er dem de siger de er. lets encrypt er en google, mozilla og microsoft bl.a. samarbejder med.
# 7. Hvorfor stoler min browser på et certifikat udstedt af let's encrypt?
lets encrypt er en google, mozilla og microsoft bl.a. samarbejder med. de har gået igennem en masse krav og regler for at blive CA
# 8. Hvorfor kan jeg se en HTTP-request i klartekst i WireShark, men ikke en HTTPS-request?
Fordi http ikke er krypteret, men det er https. http + TLS

Eksempler på spørgsmål om SSH, VPN og tunnels:
# 9. Hvordan fungerer SSH public key authentication under motorhjelmen?
client: "Hej jeg vil gerne ind" server: "Jeg har en public key. Jeg laver et tal 1234 men nu bruger jeg min public key til at skjule tallet så du får xxxx. Hvis du virkelig har tilladelse til at komme ind, så bevis det ved at læse tallet" client: "Jeg har en private key og der står 1234" server: "Okay du har tilladelse"
# 10. Hvad er forskellen på id_ed25519 og id_ed25519.pub, og hvilken af dem må man dele?
den første er private key og den anden der slutter på .pub er public key. man må aldrig dele private key men man må gerne dele public key
# 11. Hvad er en SSH tunnel (port forwarding), og hvornår er det nyttigt?
ssh tunnel er hvor per har en database på en lokal server og så sidder jytte derhjemme og vil gerne have adgang så hun bruger ssh tunnel til at få adgang til databasen derhjemmefra.

En SSH tunnel videresender en lokal port på din maskine til en port på serveren gennem en krypteret SSH-forbindelse.

Fx ssh -L 8080:localhost:3306 azureuser@server — nu kan du åbne localhost:8080 på din computer og det er faktisk databasen på port 3306 på serveren du rammer, alt igennem krypteret SSH.
# 12. Hvad er en VPN, og hvordan adskiller en VPN som WireGuard sig fra en SSH tunnel?
VPN er hvor man kan skjule sin ip adr og sige at man er en anden ip adr end man i virkeligheden er. ssh tunnel er at man kan få adgang til en specifik port så de har ikke rigtig noget tilfælles som sådan.
