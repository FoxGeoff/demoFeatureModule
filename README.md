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
    //After feature module
    AppRoutingModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```