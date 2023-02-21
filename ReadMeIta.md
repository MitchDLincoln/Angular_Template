Struttura Generale del Progetto

src
|-- app
     |-- core
       |-- [+] guards
       |-- [+] interceptors
       |-- [+] services
       |-- core.module.ts
     |-- shared
          |-- components
              |-- header
              |-- footer
              |-- button
          |-- [+] pipes
          |-- [+] directives
          |-- [+] models     
     |-- features
       |-- home
           |-- [+] components
           |-- [+] services
           |-- home-routing.module.ts
           |-- home.module.ts
       |-- awesome-widget
           |-- [+] components
           |-- [+] services
           |-- [+] models
           |-- awesome-widget.module.ts
     app.component.html
     app.component.css
     app.component.spec.ts
     app.component.ts
     app.module.ts
     app-routing.module.ts

Independent and small components

Every component should have its own reason to exist and should be as small as possible. For example, if we create a component to manage a whole page, it’ll be hard to modify because we’ll have hundreds of lines of code, but if we split that page in different components it’ll be easy to maintain since we’ll have small classes and htmls.

Reusable components

On a big application, we’ll have lots of elements with the same functionality and design (buttons, inputs, titles,…), so consider creating a component for every element we have in the application in order to give them a custom style and avoid the use of global styles.

If you are using an external component library, I would recommend wrapping the components on your own components. You might want to change the library or create a custom one, and it will help you to refactor the components.

State management

State management is mandatory if we want to have a highly scalable application. It’ll help you with loading times and API calls.

NgRx is the one to use if we are working with angular.

Get lazy

Lazy loading modules in angular is probably the most important key when building scalable applications, we just want to load what we are going to use!

Specifiche Strutture del Progetto

App Module

Angular ha bisogno di un modulo per eseguire l'avvio dell'applicazione. Viene generato automaticamente se utilizziamo Angular CLI. Importa anche AppRoutingModule, che include i percorsi principali per l'applicazione.
Questo AppModule viene creato nella cartella src/app.

Core Module

Il CoreModule è responsabile della fornitura di `services`, `interceptors` e `guards` a livello di applicazione e singleton.

Questo modulo deve essere importato una volta dall'AppModule e viene creato nella cartella src/app/core.

Under the src/app/core folder, create a services/interceptors/guards folder if needed, and then we may create a new folder for every service/interceptor/guard we want to include in this module.

Shared Module
In the SharedModuleand include every component/pipe/directive we want to share across the application. This module also imports the modules required by angular (CommonModule, FormsModule, ReactiveFormsModule,…).

This module can be imported by every other module that wants to use a shared component/pipe/directive or angular module. To be able to do it, remember to re-export the components/directives/pipes/modules you want to share. The SharedModule will be created in the src/app/shared folder.

Under the src/app/sharedfolder, create a components/pipes/directives folder if needed, and then we may create a new folder for every component/pipe/directive we want to include in this Module

Feature Module
For every feature in the application we’ll create a new module and treat it as a different project with its own folder structure.

This feature module should be created in the src/app/features/<feature-name>.

In every feature module we may include the services, components, models,… we need for this feature under the respective subfolder

On these modules we also include the routing module for the feature if needed.

Final Result
src
|-- app
     |-- core
       |-- [+] guards
       |-- [+] interceptors
       |-- [+] services
       |-- core.module.ts
     |-- shared
          |-- components
              |-- header
              |-- footer
              |-- button
          |-- [+] pipes
          |-- [+] directives
          |-- [+] models     
     |-- features
       |-- home
           |-- [+] components
           |-- [+] services
           |-- home-routing.module.ts
           |-- home.module.ts
       |-- awesome-widget
           |-- [+] components
           |-- [+] services
           |-- [+] models
           |-- awesome-widget.module.ts
     app.component.html
     app.component.css
     app.component.spec.ts
     app.component.ts
     app.module.ts
     app-routing.module.ts
Other tips to build scalable angular applications
On this article I wrote about creating a good folder structure for highly scalable application, but when building those types of applications I would also recommend to do these:

Use cache as much as possible
Don’t forget to write test
Use linters and formatters
Use a proper version control
Conclusion
Dealing with folder structure is always tricky and there isn’t a 100% correct way to do it and it’ll depends on the project you are going to work on, but I hope this article could help you to build an awesome Angular application.