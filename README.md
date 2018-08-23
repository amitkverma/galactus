# Galactus

Run `ansible-playbook -i ./hosts/production.yml server.yml -e "env=production" --private-key=./pub_keys/prod.pem`

ansible-playbook -i ./hosts/preprod.yml  preprod.yml   -e "env=preprod" --private-key=~/Documents/Keys/cerberus.pem