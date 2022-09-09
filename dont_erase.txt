ssh-keygen -t ed25519 -C "amv_mail@mail.ru"
sudo ufw disable
docker run --name yamdb -it -p 8000:8000 yamdb
python3 manage.py makemigrations
python3 manage.py migrate
pip install -r requirements.txt
source ./venv/bin/activate
deactivate
docker-compose up
docker-compose up -d --build
docker exec web python manage.py migrate
docker exec web python manage.py createsuperuser
docker exec web python manage.py collectstatic --no-input
# вход в контейнер через tty в интерактивном режиме
docker exec -ti infra-web-1 python manage.py createsuperuser
docker exec api_yamdb-web-1
docker-compose down -v
docker container start 5a6c030d551c
docker container stop 5a6c030d551c
docker exec -it 5a6c030d551c bash
docker container rm 5a6c030d551c
docker logs dfb3ae1d1dcb > ./docker.log
docker stats
docker system df
docker container prune
# установка postman
sudo snap install postman
