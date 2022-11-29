# **Angular Commands and Steps**

## **Basic commands**
---
1) To create a project.

        ng new <project-name>

2) To run the project.
        
        ng serve --open
    or

        ng s --o

3) To create a new component.

        ng generate component <component-name> --skip-tests=true
    or

        ng g c <component-name> --skip-tests=true


## **Routing Steps**
---
1) changes in app.module.ts

        const <component-name>:Routes = [
            {
                path:"",
                component:<component-class>
            },
        ]
    and add the below line in imports

        RouterModule.forRoot(<router-name>),
        
2) Add the below commands to call
        
        routerLink = "/"

## **Data binding Steps**
---
1) In \<component-name\>.component.ts file, add the below line in export class
    > if data is in JSON format
        
        <variable-name>:any = [
            {
                variable1:"value1",
                variable2:"value2",
                variable3:"value3",
            }
        ]
    > if data is a variable

        variable1="value1"

2) In corresponding HTML file, data can be displayed using the below format

    > if the data is in JSON Format, use "ngFor" to iterate through the JSON array

        <h1 *ngFor="let i of <variable-name>">
            {{i.variable1}}
        </h1>

    > If the data is a variable

        {{variable1}}


## **Two way data binding steps**
---
1) In app.module.ts file add the below line in imports

        FormModule

2) Add below line inside the /<component-name/>.component.ts file export statement

        variable1=""
        variable2=""

        <function-name>=()=>{
            let employees = {
                "variable1":this.variable1,
                "variable2":this.variable2,
            }
        }

3) In corresponding HTML file, inside the input tag, add the below code

        name="variable1" [(ngModel)]="variable1"

    >for example

        <input type="text" class="form-control" name="variable1" [(ngModel)]="variable1">
    
## **Fetch Data using Services**
---
1) Create new service

        ng g s <service-name> --skip-tests=true

2) Import HTTp module.

        import { HttpClientModule } from '@angular/common/http'

3) In app.module.ts file add the below line in imports.

        HttpClientModule

4) In \<service-name\>.service.ts file, inside export class, add below code.

        constructor(private http:HttpClient) {}
        fetchCourses = () => {
            return this.http.get('<API link>')
        }

5) Inside the correspondng component.ts file in export class add the below code.

        constructor(private api:ApiService) {
            api.fetchCourses().subscribe(
                (response)=>{
                    this.data = response
                }
            )
        }
        data:any = []