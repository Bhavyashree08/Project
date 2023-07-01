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
Firebase Realtime Database
{
  "users": {
    "user1": {
      "name": "John",
      "age": 25,
      "score": 85
    },
    "user2": {
      "name": "Emily",
      "age": 30,
      "score": 92
    },
    "user3": {
      "name": "Michael",
      "age": 21,
      "score": 78
    }
  }
}
To display the names and scores 
html
<!-- user-list.component.html -->

<!-- Import Angular Material modules -->
<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
<mat-form-field>
  <mat-label>Filter Scores</mat-label>
  <input matInput (keyup)="applyFilter($event.target.value)" placeholder="Filter">
</mat-form-field>

<table mat-table [dataSource]="dataSource" class="mat-elevation-z8">
  <!-- Columns -->
  <ng-container matColumnDef="name">
    <th mat-header-cell *matHeaderCellDef>Name</th>
    <td mat-cell *matCellDef="let user">{{ user.name }}</td>
  </ng-container>

  <ng-container matColumnDef="score">
    <th mat-header-cell *matHeaderCellDef>Score</th>
    <td mat-cell *matCellDef="let user">{{ user.score }}</td>
  </ng-container>

  <!-- Column definitions -->
  <tr mat-header-row *matHeaderRowDef="displayedColumns"></tr>
  <tr mat-row *matRowDef="let user; columns: displayedColumns;"></tr>
</table>
typescript
// user-list.component.ts

import { Component, OnInit } from '@angular/core';
import { MatTableDataSource } from '@angular/material/table';

export interface User {
  name: string;
  age: number;
  score: number;
}

@Component({
  selector: 'app-user-list',
  templateUrl: './user-list.component.html',
  styleUrls: ['./user-list.component.css']
})
export class UserListComponent implements OnInit {
  users: User[] = [
    { name: 'John', age: 18, score: 85 },
    { name: 'Emily', age: 20, score: 92 },
    { name: 'Michael', age: 21, score: 78 }
  ];

  displayedColumns: string[] = ['name', 'score'];
  dataSource = new MatTableDataSource<User>();

  ngOnInit() {
    this.dataSource.data = this.users.filter(user => user.age < 21);
  }

  applyFilter(filterValue: string) {
    this.dataSource.filter = filterValue.trim().toLowerCase();
  }
}



 
   
