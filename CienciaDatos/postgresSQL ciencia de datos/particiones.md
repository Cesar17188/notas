# Particiones

Otra de las caracteristicas muy interesantes y muy practicas que no todos los navegadores nos ofrecen es el uso de particiones [[particiones y agregacion]](véase el curso de Introduccion a Postgres de Platzi) de manera explicita.

Todos los manejadores hacen el particionado internamente para segmentar los datos y aumentar el performance, postgres permite hacer particiones custom (mes,año, etc), esta estrategia es muy buena y poderosa, sin embargo no todas las tablas deben ser particionadas.

**Una desventaja del particionado es que no puedes tener una sola clave única o id, por lo que esas llaves primaria no existen y no existe la consistencia de datos**, aquí el indice sera el campo por el que filtras. En contraste son buenísimas para los dashboards, ya que la informacion siempre esta segmentada y es inmediata (siempre hay un trade-off).