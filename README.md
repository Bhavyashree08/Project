# Project
Angular project
ng new my-interface
cd my-interface
ng generate component top-bar
ng generate component tab1
ng generate component tab2
ng generate component tab3
html
<nav>
  <ul>
    <li><a routerLink="/tab1">Tab 1</a></li>
    <li><a routerLink="/tab2">Tab 2</a></li>
    <li><a routerLink="/tab3">Tab 3</a></li>
  </ul>
</nav>
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { Tab1Component } from './tab1/tab1.component';
import { Tab2Component } from './tab2/tab2.component';
import { Tab3Component } from './tab3/tab3.component';

const routes: Routes = [
  { path: 'tab1', component: Tab1Component },
  { path: 'tab2', component: Tab2Component },
  { path: 'tab3', component: Tab3Component },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
<app-top-bar></app-top-bar>
<router-outlet></router-outlet>
ng serve
