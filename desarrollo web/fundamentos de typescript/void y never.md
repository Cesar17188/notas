# Void y never

**Tipo Void:** Representa la ausencia de tipo. usado en funciones que no retornan nada.  
**Tipo Never:** Representa funciones que lanzan excepciones o nunca retornan un valor.

**Tipo Void:** Son funciones que no necesitan de un retorno, por lo que al asignar el tipo void se sobre entiende que estas funciones retornan un undefind o un valor no definido, mas si permiten el uso de este return con este valor, que en el futuro puede ser usado para la terminacion de una funcion de este tipo.

**Tipo Never:** En este caso son funciones que nunca retornaran un valor, dentro de TS si intentas retornar un valor en una funcion Never te marcara error, normalmente usada para errores ya que son funciones que no retornan un valor sino que lanzan o arrojan un error o mensaje al ejecutarse, cabe destacar tambien que las variables declaradas como nulas no permiten que se les asigne ningun tipo de dato, caso contrario a los void que permite la asignacion del dato undefind

```ts
// type void for functions
// Explicit type

function showInfo(user: any): any {
  console.log(`User Info ${user.id} ${user.username} ${user.firstname}`);
  //   return 'hola';
}

showInfo({id: 1, username: 'Antúnez Durán', firstname: 'Francisco Javier'});

// Inferred type
function showFormattedInfo(user: any) {
  console.log(`User Info,
        id: ${user.id}
        username: ${user.username}
        firstname: ${user.firstname}`);
}

showFormattedInfo({id: 1, username: 'Antúnez Durán', firstname: 'Francisco Javier'});

// Type void as variable data type
let unusable: void;
// unusable = null; --> colocar "strict": false en tsconfig.json para poder hacer uso
unusable = undefined;

// Type never
function handleError(code: number, message: string): never {
  // Process your code
  // Generate a message
  throw new Error(`${message}. Code: ${code}`);
}

try {
  console.log('La funcion handleError no devuelve nada bajo esta linea');
  handleError(404, 'Not found');
} catch (error) {}

function sumNumbers(limit: number): never {
  let sum = 0;
  while (true) {
    sum++;
  }
  // return sum;
}

sumNumbers(10); // --> Llamada a un bucle infinito no acabaria nunca, typescript no compila, al verlo.

```