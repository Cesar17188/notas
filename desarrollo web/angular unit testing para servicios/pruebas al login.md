# Pruebas al login
para poder hacer pruebas al login es basicamente verificar el autentificador de Auth.service

auth.model.ts
```ts
export interface Auth {
  access_token: string;
}
```

auth.service.ts
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { switchMap, tap } from 'rxjs/operators';
import { BehaviorSubject } from 'rxjs';

import { environment } from './../../environments/environment';
import { Auth } from './../models/auth.model';
import { User } from './../models/user.model';
import { TokenService } from './../services/token.service';

@Injectable({
  providedIn: 'root'
})
export class AuthService {

  private apiUrl = `${environment.API_URL}/api/v1/auth`;
  private user = new BehaviorSubject<User | null>(null);
  user$ = this.user.asObservable();

  constructor(
    private http: HttpClient,
    private tokenService: TokenService
  ) {
  }

  getCurrentUser() {
    const token = this.tokenService.getToken();
    if (token) {
      this.getProfile()
      .subscribe()
    }
  }

  login(email: string, password: string) {
    return this.http.post<Auth>(`${this.apiUrl}/login`, {email, password})
    .pipe(
      tap(response => this.tokenService.saveToken(response.access_token)),
    );
  }

  getProfile() {
    return this.http.get<User>(`${this.apiUrl}/profile`)
    .pipe(
      tap(user => this.user.next(user))
    );
  }

  loginAndGet(email: string, password: string) {
    return this.login(email, password)
    .pipe(
      switchMap(() => this.getProfile()),
    )
  }

  logout() {
    this.tokenService.removeToken();
    this.user.next(null);
  }
}
```

auth.service.spec.ts
```ts
import { TestBed } from '@angular/core/testing';
import { HttpClientTestingModule, HttpTestingController } from '@angular/common/http/testing';

import { AuthService } from './auth.service';
import { TokenService } from './token.service';
import { Auth } from '../models/auth.model';
import { environment } from '../../environments/environment';

fdescribe('AuthService', () => {
  let authService: AuthService;
  let httpController: HttpTestingController;
  let tokenService: TokenService;

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        HttpClientTestingModule
      ],
      providers: [
        AuthService,
        TokenService
      ]
    });
    authService = TestBed.inject(AuthService);
    httpController = TestBed.inject(HttpTestingController);
    tokenService = TestBed.inject(TokenService);
  });

  afterEach(() => {
    httpController.verify();
  });

  it('should be create', () => {
    expect(authService).toBeTruthy();
  });

  describe('test for login', () => {
    it('should return a token', (doneFn) => {
      //Arrange
      const mockData: Auth = {
        access_token: '121212'
      };
      const email = 'cesar@gmail.com';
      const password = '1212';
      //Act
      authService.login(email, password).subscribe((data) => {
        //Assert
        expect(data).toEqual(mockData);
        doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/auth/login`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
    });
  });

  it('should call to saveToken', (doneFn) => {
    //Arrange
    const mockData: Auth = {
      access_token: '121212'
    };
    const email = 'cesar@gmail.com';
    const password = '1212';
    spyOn(tokenService, 'saveToken').and.callThrough();
    //Act
    authService.login(email, password).subscribe((data) => {
      //Assert
      expect(data).toEqual(mockData);
      expect(tokenService.saveToken).toHaveBeenCalledTimes(1);
      expect(tokenService.saveToken).toHaveBeenCalledOnceWith('121212');
      doneFn();
    });
    //http config
    const url = `${environment.API_URL}/api/v1/auth/login`;
    const req = httpController.expectOne(url);
    req.flush(mockData);
  });
});
```