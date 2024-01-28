pip freeze >requirements.txt


chmod +x ./entrypoint.sh

docker-compose build
docker-compose up -d

python manage.py startapp taskapp

#Empezar terminal del container
docker exec -it django /bin/sh
./manage.py shell
from newapp.tasks import tp1, tp2, tp3, tp4

tp1.delay()
tp2.delay()
tp3.delay()
tp4.delay()
