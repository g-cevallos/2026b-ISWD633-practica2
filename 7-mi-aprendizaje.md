# Aprendizaje 
Estas configuraciones son fundamentales para el día a día en un entorno laboral real. Por ejemplo, en una empresa, saber limitar el uso de memoria y procesador evita que una sola aplicación consuma todos los recursos y termine colapsando los servidores, lo que ayuda a mantener la estabilidad general y a controlar los costos si se usan servicios de pago. Por otro lado, implementar correctamente los Healthchecks y las políticas de reinicio significa que las aplicaciones adquieren la capacidad de recuperarse solas ante cualquier fallo; esto es invaluable en el trabajo real, ya que garantiza que el servicio siga disponible para los clientes sin que un desarrollador o administrador tenga que intervenir manualmente.
# Problema
Durante el desarrollo del ejercicio, el único problema que se presentó fue al intentar construir la imagen basada en CentOS:7, ya que el sistema arrojaba un error de conexión. Esto ocurre porque ciertas versiones de CentOS ya no tienen soporte oficial y sus repositorios fueron movidos.
Para solucionarlo se modificó el archivo Dockerfile, se usó el comando sed para buscar y comentar las listas de espejos y reemplazar la URL base antigua por la del nuevo repositorio histórico (vault.centos.org). Se agregó la siguiente línea:
```
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```
