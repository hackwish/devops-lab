# DevOps Workshop

## Initialize Gitlab
docker-compose up

docker network ls

docker network inspect gitlab_default
docker network inspect gitlab_default | grep -A3 gitlab_gitlab_1
docker network inspect gitlab_default | grep -A3 gitlab_gitlab_1 | grep IPv4
docker network inspect gitlab_default | grep -A3 gitlab_gitlab_1 | grep IPv4 | awk '{print $2}' | tr -d \",


```
docker exec -it gitlab_gitlabrunner_1 \
	gitlab-runner register -n \
		--url http://gitlab-dev:8090 \
		--registration-token 9ZQmhw7VUnwqKnaHVRSJ \
		--docker-extra-hosts gitlab-dev:172.23.0.3 \
		--executor docker \
		--description "Docker Runner" \
		--docker-image docker:latest \
		--docker-network-mode gitlab_default \
		--docker-volumes "/var/run/docker.sock:/var/run/docker.sock" \
		--docker-privileged
```
## Work on Test App
cd test-app
docker build -t test-app .
docker run --rm -p8000:80 test-app

git config --global user.name "Administrator"
git config --global user.email "admin@example.com"

Ir a Gitlab: http://127.0.0.1:8090/
crear repo "test-app"

git init
git remote add origin http://gitlab-dev:8090/root/test-app.git
git add .
git commit -m "Initial commit"
git push -u origin master

