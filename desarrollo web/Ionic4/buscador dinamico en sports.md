# RETO: Buscador dinámico en Sports

primero crearemos un nuevo metodo en el servicio de platzimusic

platzi-music.service.ts
```ts
private urlapi = 'https://platzi-music-api.herokuapp.com';

searchTracks(keywords) {
    return this.http.get(`${this.urlapi}/search?q=${keywords}&type=track`);
  }
```

crearemos un archivo llamado songs.model.ts, dentro de una carpeta llamada models para poder exportar la interfaz de song

song.model.ts
```ts
export interface Song {
  name?: string;
  playing: boolean;
  // eslint-disable-next-line @typescript-eslint/naming-convention
  preview_url?: string;
  tracks?: string[];
};
```

ahora se podrán hacer los cambios en sports page

sports.page.ts
```ts
import { Song } from '../../models/song.model';
import { PlatziMusicService } from '../services/platzi-music.service';

export class SportsPage {

  currentCenter: any;
  coordinates: google.maps.LatLngLiteral[] = [];
  defaultZoom = 14;
  center: google.maps.LatLngLiteral;
  searching = false;
  text = 'Ingrese la canción a buscar';
  songs: Song[];
  song: Song;
  currentSong: HTMLAudioElement;

  constructor(
    private songService: PlatziMusicService
  ) { }

  ionViewDidEnter() {
    this.getCurrentPosition();
    this.watchPosition();
  }

  async getCurrentPosition() {
    const coordinates = await Geolocation.getCurrentPosition();
    this.currentCenter = {
      lat: coordinates.coords.latitude,
      lng: coordinates.coords.longitude
    };
    this.center = {
      lat: coordinates.coords.latitude,
      lng: coordinates.coords.longitude
    };
  }

  watchPosition() {
    Geolocation.watchPosition({}, position=> {
      this.center = {
        lat: position.coords.latitude,
        lng: position.coords.longitude
      };
      this.coordinates.push ({
        lat: position.coords.latitude,
        lng: position.coords.longitude
      });
    });
  }

  async getTracks(keywords) {
    this.searching = true;
    if(keywords.length > 0) {
      this.songService.searchTracks(keywords)
      .subscribe(async resp => {
        // eslint-disable-next-line @typescript-eslint/dot-notation
        this.songs = await resp['tracks'].items
        .filter((item: any) => item.preview_url);
        if (this.songs.length === 0) {
          this.text = 'No hay resultados de la busqueda.';
        }
        this.searching = false;
      });
    } else {
      this.text = 'Ingrese una canción a la busqueda';
      this.songs = [];
    }
  }

  play(song: Song) {
    if ( this.currentSong) {
      this.pause();
    }
    this.song = song;
    this.currentSong = new Audio(this.song.preview_url);
    this.currentSong.play();
    this.currentSong.addEventListener('ended', () =>
    this.song.playing = false);
    this.song.playing = true;
  }

  pause() {
    this.currentSong.pause();
    this.song.playing = false;
  }
}

```