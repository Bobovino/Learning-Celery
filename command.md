pip freeze >requirements.txt

chmod +x ./entrypoint.sh

docker-compose build
docker-compose up -d

python manage.py startapp taskapp

#Empezar terminal del container
docker exec -it django /bin/sh
./manage.py shell

#Execute tasks
from newapp.tasks import tp1, tp2, tp3, tp4
tp1.delay()
tp2.delay()
tp3.delay()
tp4.delay()

#Task grouping
from newapp.tasks import tp1, tp2, tp3, tp4
from celery import group
task_group= group(tp1.s(), tp2.s(), tp3.s(), tp4.s())
task_group.apply_async()

#Task chaining
from newapp.tasks import tp1, tp2, tp3, tp4
from celery import chain

task_chain=chain(tp1.s(), tp2.s(), tp3.s())
task_chain.apply_async()

