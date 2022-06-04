# Descarga de archivos con Http

creamos el servicio de descarga de archivos
```
ng g s services/files
```

dentro del servicio importamos el httpClient que tiene por defecto una forma de descargar archivos

files.service.ts
```ts

import { Injectable } from '@angular/core';

import { HttpClient } from '@angular/common/http';

  

import { saveAs } from 'file-saver'

import { tap, map } from 'rxjs/operators';

  

@Injectable({

 providedIn: 'root'

})

export class FilesService {

  

 constructor(

 private http: HttpClient

 ) { }

  

 getFile(name: string, url: string, type: string) {

	 return this.http.get(url, {responseType: 'blob'})

	 .pipe(

		 tap(content => {

			 const blob = new Blob([content], {type});

			 saveAs(blob, name);

		 }),

		 map(() => true)

		 );

	 }

	}
```

despues vamos al app component donde ingresaremos una función para descargar archivos con el servicio file service 
app.component.ts

```ts
import { FilesService } from './services/files.service';

constructor(

 private usersService: UsersService,

 private filesService: FilesService

 ) { }
 

downloadPdf() {

 this.filesService.getFile('my.pdf', 'https://young-sands-07814.herokuapp.com/api/files/dummy.pdf', 'application/pdf')

 .subscribe()

 }

```

finalmente creamos el botón de llamada a la acción en app component

app.component.html
```html
<p>

 <button (click)="downloadPdf()">Descargar PDF</button>

</p>
```