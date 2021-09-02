# Despliegue

Después de realizar el despliegue, siguiendo los [siguientes pasos](https://docs.getodk.org/central-install-digital-ocean/#central-install-digital-ocean-advanced), el contenedor de Nginx no podrá generar el certificado ssl correctamente. Para solucionarlo debemos ingresar al contenedor de nginx, de la siguiente forma:

```bash
docker exec -it central_nginx_1 sh
```

Y correr el siguiente comando:
```bash
openssl dhparam -out /etc/dh/nginx.pem 2048
```

Luego, debemos detener los servicios de docker compose, y volver a iniciarlos para que el nginx se reinicie con los nuevos parámetros (NO reconstruir los contenedores para que no se pierdan los cambios)