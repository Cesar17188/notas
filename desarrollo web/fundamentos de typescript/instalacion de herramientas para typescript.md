# Instalación de herramientas para TypeScript

Instrucciones de instalacion de NVM en Windows

[https://docs.microsoft.com/en-us/windows/nodejs/setup-on-windows](https://docs.microsoft.com/en-us/windows/nodejs/setup-on-windows)

Les recomiendo utilizar un gestor de paquetes para hacer la instalación de librerías como Node y otros programas. En el caso de Mac pueden utilizar [Homebrew](https://brew.sh/) o [Macports](https://www.macports.org/install.php), en Windows acaban de sacar [Winget](https://github.com/microsoft/winget-cli) o puedes usar Chocolatey y si usas Linux… ya sabes de lo que te hablo.

1.  Instalar NodeJs -> luego de tener instalado Node, se puede usar npm. Entonces,

```
npm install -g typescript
```

1.  Crean un folder. Y dentro del folder crean un archivo .ts. Entonces dentro del folder, hacen:

```
touch index.ts
```

1.  Este es un ejemplo de algo que hice para probar TS:

```
class Payment {
    private bin: number;
    private cvc: number;
    private year: number;

    constructor( bin: number, cvc: number, year: number ) {
        this.bin = bin;
        this.cvc = cvc;
        this.year = year
    }
        
    private validateBin () {
        return true
    }

    private validateCVC () {
        return true
    }

    private validateYear () {
        return true
    }

    makePayment() {
        if (this.validateBin() && this.validateCVC() && this.validateYear() )
        {
            return 'Pago exitoso'
        }
        else {
            return 'no se pudo :/'
        }
    }

}

let pay = new Payment(123456789012345, 345, 2028)
console.log(pay.makePayment())
```

1.  para compilar el código, en consola escriben

```
npx tsc index.ts --outFile dist/index.js
```