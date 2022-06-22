# jenkins_docker
Deploy de jenkins con docker de imagen custom con docker dentro


importante despues de la build de la imagen y levantamiento del contenedor hacer lo siguiente:

1. entrar al contenedor de jenkins como usuario root: docker exec -ti -u root jenkins bash
2. dar permisos al sock: chwon jenkins var/run/docker.sock
3. listo