# Angular 11 JWT Authentication example

## Flow for User Registration and User Login
For JWT – Token based Authentication with Web API, we’re gonna call 2 endpoints:
- POST `api/auth/signup` for User Registration
- POST `api/auth/signin` for User Login

You can take a look at following flow to have an overview of Requests and Responses that Angular 10 Client will make or receive.

![angular-11-jwt-authentication-flow](angular-11-jwt-authentication-flow.png)

## Angular JWT App Diagram with Router and HttpInterceptor
![angular-11-jwt-authentication-overview](angular-11-jwt-authentication-overview.png)

For more detail, please visit:
> [Angular 11 JWT Authentication & Authorization with Web API](https://bezkoder.com/angular-11-jwt-auth/)

## With Spring Boot back-end

> [Angular + Spring Boot: JWT Authentication & Authorization example](https://bezkoder.com/angular-11-spring-boot-jwt-auth/)

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`.

## With Node.js Express back-end

> [Angular + Node.js Express: JWT Authentication & Authorization example](https://bezkoder.com/node-js-express-angular-10-jwt-auth/)

Open `app/_helpers/auth.interceptor.js`, modify the code to work with **x-access-token** like this:
```js
...

// const TOKEN_HEADER_KEY = 'Authorization'; // for Spring Boot back-end
const TOKEN_HEADER_KEY = 'x-access-token';   // for Node.js Express back-end

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  ...

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    ...
    if (token != null) {
      // for Spring Boot back-end
      // authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, 'Bearer ' + token) });

      // for Node.js Express back-end
      authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, token) });
    }
    return next.handle(authReq);
  }
}

...
```

Run `ng serve --port 8081` for a dev server. Navigate to `http://localhost:8081/`.

## More practice

> [Angular CRUD application example with Web API](https://bezkoder.com/angular-10-crud-app/)

> [Angular Pagination example | ngx-pagination](https://github.com/bezkoder/angular-10-pagination-example)

> [Angular File Upload example with progress bar](https://bezkoder.com/angular-10-file-upload/)

Fullstack with Node.js Express:
> [Angular + Node.js Express + MySQL](https://bezkoder.com/angular-10-node-js-express-mysql/)

> [Angular + Node.js Express + PostgreSQL](https://bezkoder.com/angular-10-node-express-postgresql/)

> [Angular + Node.js Express + MongoDB](https://bezkoder.com/angular-10-mongodb-node-express/)

Fullstack with Spring Boot:
> [Angular + Spring Boot + MySQL](https://bezkoder.com/angular-10-spring-boot-crud/)

> [Angular + Spring Boot + PostgreSQL](https://bezkoder.com/angular-10-spring-boot-postgresql/)

> [Angular + Spring Boot + MongoDB](https://bezkoder.com/angular-10-spring-boot-mongodb/)

Fullstack with Django:
> [Angular + Django Rest Framework](https://bezkoder.com/django-angular-10-crud-rest-framework/)

Integration (run back-end & front-end on same server/port)
> [How to Integrate Angular 10 with Node.js Restful Services](https://bezkoder.com/integrate-angular-10-node-js/)

> [How to Integrate Angular with Spring Boot Rest API](https://bezkoder.com/integrate-angular-spring-boot/)