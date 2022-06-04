# Construyendo nuestro reproductor

dentro del footer del home.page.html hacemos los siguientes cambios


home.page.html
```html

<ion-footer>
	 <ion-grid>
		 <ion-row>
			 <ion-col class="ion-text-start">0:00</ion-col>
			 <ion-col class="ion-text-end">0:00</ion-col>
		 </ion-row>
	 </ion-grid>
	 <ion-progress-bar [value]="0.5"></ion-progress-bar>
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

home.page.ts
```ts
interface Song {
 name?: string;
 playing: boolean;
}

song: Song = {
 name: '',
 playing:false
 };

play(){
	 this.song.playing=true;
 }

 pause(){
	 this.song.playing=false;
 }
```