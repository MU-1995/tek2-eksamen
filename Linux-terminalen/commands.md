# /SSH/
```bash
ssh -i ~/downloads/tek-eks-vm_key.pem azureuser@20.91.143.54
```
# /Mapper og filer/
mkdir minmappe

cd minmappe

cd ..

ls

ls -la

pwd

nano minfil.txt

cat minfil.txt

echo "nyt indhold" > minfil.txt

echo "nyt indhold" >> minfil.txt
# /Søg i filer/
cat minfil.txt

head -1 minfil.txt

tail -1 minfil.txt

less minfil.txt

grep "søgeord" minfil.txt
# /pipe og redirect/
ls -la | grep ".txt"

ls -la > minfil.txt

ls -la >> minfil.txt
# /filrettigheder/
ls -la

chmod 755 minfil.txt
# /SCP/
```bash
scp -i ~/downloads/tek-eks-vm_key.pem minfil.txt azureuser@20.91.143.54:~/
```
