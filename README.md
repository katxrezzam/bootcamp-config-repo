# bootcamp-config-repo

Repositorio de configuracion externalizada para el `config-server` (Spring Cloud Config) del
sistema bancario de `proyecto-bootcamp`. No contiene codigo, solo archivos de configuracion.

## Estado actual

Vacio / plantilla. Se llena a partir de la Fase 1, cuando `config-server` este operativo y los
microservicios empiecen a dejar de usar su `application.yml` local.

## Convencion de nombres (a aplicar cuando se agreguen los primeros archivos)

- `application.yml` — configuracion compartida por todos los microservicios (por ejemplo,
  formato de logs, timeouts por defecto de Resilience4j).
- `<nombre-del-servicio>.yml` — configuracion especifica de cada servicio, con el mismo nombre
  que su `spring.application.name` (por ejemplo `customer-service.yml`, `account-service.yml`).
- `<nombre-del-servicio>-<profile>.yml` — variantes por profile (`dev`, `docker`, etc.) cuando
  hagan falta, siguiendo la convencion estandar de Spring Cloud Config.

## Por que un repo aparte

Spring Cloud Config Server sirve configuracion leyendo un repo Git (local o remoto) distinto del
codigo de los microservicios. Mantenerlo separado permite versionar y auditar cambios de
configuracion (credenciales de conexion, flags, limites de negocio) independientemente de los
despliegues de codigo — relevante en un dominio bancario donde esos cambios tambien deben quedar
trazables.
