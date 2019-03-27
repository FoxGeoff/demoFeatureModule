# DemoFeatureModule

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.1.3.

* Routing for components in feature modules: NOTE 'AppRoutingModule' must be called after 'CustomerDashboardModule'
```
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    CustomerDashboardModule,
    //After all feature module
    AppRoutingModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
#Activated Route in action:
```
How does the target HeroDetailComponent learn about that id? Don't analyze the URL. Let the router do it.
The router extracts the route parameter (id:15) from the URL and supplies it to the HeroDetailComponent via the ActivatedRoute service.
```
* Route definition with a parameter
* ```localhost:4200/hero/15```
* ```{ path: 'hero/:id', component: HeroDetailComponent }```
* Add to component (detail): 
*    ```import { Router, ActivatedRoute, ParamMap } from '@angular/router';```
*    ```import { switchMap } from 'rxjs/operators';```
* DI in constructor:
```
constructor(
  private route: ActivatedRoute,
  private router: Router,
  private service: HeroService
) {}
```
* Calling:
```
ngOnInit() {
  this.hero$ = this.route.paramMap.pipe(
    switchMap((params: ParamMap) =>
      this.service.getHero(params.get('id')))
  );
}
```
* API Ref: https://angular.io/guide/router#parammap-api

