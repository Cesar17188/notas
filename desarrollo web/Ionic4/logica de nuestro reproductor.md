# Lógica de nuestro reproductor

Vamos a conectar con la canción seleccionada y dar los tiempos de reproducción en nuestro homepage

hay que hacer los cambios en home.page.ts

home.page.ts
```ts
// Cambio en variables
interface Song {
 name?: string;
 playing: boolean;
 // eslint-disable-next-line @typescript-eslint/naming-convention
 preview_url?: string;
}

 song: Song = {
	 name: '',
	 playing:false,
	 // eslint-disable-next-line @typescript-eslint/naming-convention
	 preview_url: ''
 };
 currentSong: any = {};
 newTime: any;


// Cambio en funciones
play(){
	 this.currentSong = new Audio(this.song.preview_url);
	 this.currentSong.play();
	 this.currentSong.addEventListener('timeupdate', () => {
	 this.newTime = (this.currentSong.currentTime * (this.currentSong.duration / 10)) / 100;
	 });
	 this.song.playing=true;
 }

 pause(){
	 this.currentSong.pause();
	 this.song.playing=false;
 }

 parseTime(time='0.00') {
	 if (time) {
		 const partTime = parseInt(time.toString().split('.')[0], 10);
		 let minutes = Math.floor(partTime/60).toString();
			 if(minutes.length === 1) {
					minutes = '0'+minutes;
		 }
		 let seconds = (partTime%60).toString();
			 if(seconds.length === 1) {
					seconds = '0'+seconds;
		 }
	return minutes + ':' + seconds;
	 }
 }
```

posteriomente hacemos los cambios en el ion-footer de nuestro homepage.html

```html
<ion-footer>
	 <ion-grid>
		 <ion-row>
			 <ion-col class="ion-text-start">{{ parseTime(currentSong.currentTime) || "0:00"}}</ion-col>
			 <ion-col class="ion-text-end">{{ parseTime(currentSong.duration) || "0:00"}}</ion-col>
		 </ion-row>
	 </ion-grid>
	 <ion-progress-bar [value]="newTime"></ion-progress-bar>
		 <ion-grid>
			 <ion-row>
				 <ion-col size="1">
					 <ion-icon name="heart"></ion-icon>
				 </ion-col>
				 <ion-col size="10">
					 <ion-text>{{ song.name || "Aun no has seleccionado canción"}}</ion-text>
				 </ion-col>
				 <ion-col size="1">
					 <ion-icon name="play" (click)="play()" *ngIf="!song.playing"></ion-icon>
					 <ion-icon name="pause" (click)="pause()" *ngIf="song.playing"></ion-icon>
				 </ion-col>
			 </ion-row>
		 </ion-grid>
</ion-footer>
```