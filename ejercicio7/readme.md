Este archivo corre un servicio web y un servicio de base de datos, cada uno en un contenedor distinto, dando dos contenedores en total.

El contenedor "web" esta basado en la imagen "nicopaez/jobvacancy-ruby:1.3.0" y el contenedor "db" esta basado en la imagen "postgres".


```
version: '2' # Versión de compose 
services: # Definición de servicios
  web: # Nombre del servicio
    image: nicopaez/jobvacancy-ruby:1.3.0 -> La imagen base
    links: # Alias extras 
      - db
    ports: # Mapeo de puertos
      - "3000:3000"
    environment: # Variables de entorno
      PORT: "3000"
      RACK_ENV: "production"
      DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres"
    depends_on: # Indica los servicios de los cuales este servicio depende
      - db
  db: # Nombre del segundo servicio
    image: postgres # Imagen base
    environment: # Variables de entorno
      POSTGRES_PASSWORD: Passw0rd!

```


Los contenedores se ven entre sí porque el engine levanta una red virtual en la cual todos los containers pueden verse y comunicarse entre sí.
