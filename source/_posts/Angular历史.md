---
title:Angular 历史
---
From : [点我](https://medium.com/@lifenshades/difference-among-angular-8-7-6-5-4-3-2-breakdown-new-features-and-changes-811fb5f8e6f0)
#Angular 2(typescript)
1. Component-based instead of Controller
2. ES6
3. Mobile (low-end) device

#Angular 3
1. single repo for everthiing @angular/core @angular/compiler @angular/router
2. router realsing (MonoRepo)

#Angular 4
1. underlying concecpt (same or inheritance from 2)
2. reduce size of AOT compiler
3. Typescript 2.1
4. seperate @angular/core to @angular/animation
5. block in *ngIF introduced:

``` 
	*ngIf=”yourCondition; else myFalsyTemplate”s
	“<ng-template #myFalsyTemplate>Else Html</ng-template>”
```

#Angular 5
1. HttpClient : a new modulr
2. exportAs: multiply names suport for both directives and component
3. new Router Life-cycle Events:
  * ActivationStart, ActivationEnd,
  * ChildActivationStart, ChildActivationEnd,
  * GuardsCheckStart, GuardsCheckEnd, 
  * ResolveStart and ResolveEnd.

#Angular 6
1. More tool-chain and less underlying framework
2. RxJs 6
3. Synchronizes major version : 
	* Angular framework
	* Angular CLI
	* Angular Material + CDK
	* `<ng-template>` instead of `<template>`
	* Injectable
	* From 
        ```
            // app.module.ts
            import {MyService} from './my-service';
            providers: [...MyService]
        ```
	   to
	    ```javascript
			// MyService.ts
			@Injectable({ providedIn: 'root'})
			export class MyService{}
	    ```
4. 
#Angular 7

#Angular 8	
	