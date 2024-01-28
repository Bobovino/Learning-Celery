pip freeze >requirements.txt


chmod +x ./entrypoint.sh

docker-compose build
docker-compose up -d

python manage.py startapp taskapp

#Empezar terminal del container
docker exec -it django /bin/sh
./manage.py shell
