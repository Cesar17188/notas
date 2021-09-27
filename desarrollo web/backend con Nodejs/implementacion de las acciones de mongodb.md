# Implementación de las acciones de MongoDB

Las acciones son básicamente lo que es compatible con el CRUD:
![[Pasted image 20210901202035.png]]

Documentación de mongo:

-   [Collection Methods](https://docs.mongodb.com/manual/reference/method/js-collection/)
-   [MongoDB CRUD operations](https://docs.mongodb.com/manual/crud/)
-   [Mongo introduction Book](https://github.com/uokesita/the-little-mongodb-book/blob/master/es/mongodb.markdown)

Implementaremos nuestros las acciones con Mongo:
```js
class MongoLib {
  constructor() {
    this.client = new MongoClient(MONGO_URI, { useNewUrlParser: true });
    this.dbName = DB_NAME;
  }
// Todos necesiatan retornas el método connect, y connect lo que nos retorna es una promesa
  // nos devuelve una instancia a la base de datos y esa instancia de la bd tiene los métodos de mongo.
  getAll(collection, query) {
    return this.connect().then(db => {
      return db
        .collection(collection)
        .find(query)
        .toArray();
    });
  }
  get(collection, id) {
    return this.connect().then(db => {
      return db.collection(collection).findOne({ _id: ObjectId(id) });
    });
  }
  create(collection, data) {
    return this.connect()
      .then(db => {
        return db.collection(collection).insertOne(data);
      })
      .then(result => result.insertedId);
  }
  updated(collection, id, data) {
    return this.connect()
      .then(db => {
        return db
          .collection(collection)
          .updateOne({ _id: ObjectId(id) }, { $set: data }, { upsert: true });
      })
      .then(result => result.updsertdId || id);
  }
  delete(collection, id) {
    return this.connect()
      .then(db => db.collection(collection).deleteOne({ _id: ObjectId(id) }))
      .then(() => id);
  }
}
```
Ya que hemos implementado nuestras acciones en la librería de mongo, en nuestra capa de servicios podemos remover los mocks, usar directamente está librería y así tener persistencia en la base de datos.