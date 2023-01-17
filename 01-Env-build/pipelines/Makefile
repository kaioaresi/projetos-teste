docker-build:
	sed 's/<PASSWORD>/$(MYSQL_PASSWORD)/g' include/create_developer.template > include/create_developer.sql

	docker build . -t $(IMAGE)

	docker container run --name teste-k -itd --rm -e MYSQL_ROOT_PASSWORD=$(MYSQL_PASSWORD) -p 3306:3306 $(IMAGE)
	
	sleep 30

	docker container exec teste-k /bin/bash -c 'mysql --user="root" --password="$(MYSQL_PASSWORD)" < /scripts/create_developer.sql'
