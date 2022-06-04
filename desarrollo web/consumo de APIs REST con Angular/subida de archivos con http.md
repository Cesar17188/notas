# Subida de archivos con Http

otra de las tareas muy comunes es adjuntar una foto, subir un pdf, adjuntar un archivo.
Esto lo podriamos hacer desde http
En este caso se envia de una forma especial ya que no se envia un JSON sino un binario que no es un archivo como tal

file.service.ts
```ts

interface File {

 originalName: string;

 fileName: string;

 location: string;

}

uploadFile (file: Blob) {

 const dto = new FormData();

 dto.append('file', file);

 return this.http.post<File>(`${this.apiUrl}/upload`, dto, {

 // headers: {

 //   'Content-type': "multipart/form-data"

 // }

 })

 }
```


app.component.ts
```ts

onUpload(event: Event) {

 const element = event.target as HTMLInputElement;

 const file = element.files?.item(0);

 if (file) {

 this.filesService.uploadFile(file)

 .subscribe(rta => {

 this.imgRta = rta.location;

 });

 }

  

 }
```


app.component.html
```html
<p>

 <input type="file" (change)="onUpload($event)">

 <img *ngIf="imgRta" [src]="imgRta">

</p>
```