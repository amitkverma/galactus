Export Gitlab

git clone --mirror https://github.com/raveren/kint
cd kint.git
git remote add gitlab http://gitlab.example.com/raveren/kint.git
git push gitlab --mirror

Replace in system
git remote remove origin
git remote add origin http://gitlab.example.com/raveren/kint.git
git fetch --all

Follow this to have runner

https://www.digitalocean.com/community/tutorials/how-to-set-up-continuous-integration-pipelines-with-gitlab-ci-on-ubuntu-16-04

https://docs.gitlab.com/runner/commands/
and 
install docker in machine
apt install docker.io


Gitlab work
1. Install gitlab - ok
2. Check if it's working for https - ok
3. Check send email working or not while creating user - ok
4. Install gitlab-runner and docker on server 
5. Deploy Test Node repo to check if CI-CD working -> build ( on master merge ) -> test -> (create tag) finish
6. Enable gitlab backup on s3


https://cloudkul.com/blog/automate-gitlab-backups-within-amazon-s3-bucket/

