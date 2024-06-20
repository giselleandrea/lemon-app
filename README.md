# README

- APP creada en Junio de  2024 
- Autor: Giselle Quiceno

## DEPENDENCIES

* Backend lemonevent:
- Rails version
```bash
    rails "7.1.3"
```
- Ruby version
```bash
    ruby 3.1.4
```
- Instalations gems
```bash
    bundle install
```
- Database PostgreSQL
```bash
    psql (PostgreSQL) 14.12
```
- Migration
```bash
    rails db:migrate
```

* Frontend lemonfront:
- Node version
```bash
    v20.14.0
```
- npm version
```bash
    10.7.0
```
- React version
```bash
    react": "^18.3.1"
```
- Instalations 
```bash
    npm install
```

## Clonar repositorios 
- En la unidad clonar el repositorio principal lemon-app
```bash
    git clone https://github.com/giselleandrea/lemon-app
``` 
--Entrar a cada submodulo correspondiente y clonar los repositorios tanto del back como del front
```bash
    cd /lemon-app/lemonevent 
    git clone  https://github.com/giselleandrea/lemonevent

    cd /lemon-app/lemonfront 
    git clone https://github.com/giselleandrea/lemonfront
``` 

## RUNNING 
* Backend Ubicacion /lemonapp/lemonevent
```bash
    rails server

    default http://localhost:3000 
```    
* Frontend Ubicacion /lemonapp/lemonfront
```bash
    npm start

    default http://localhost:3001 
```    
## DOCKER
* Ubicacion /lemonapp
- Version
```bash
    Docker version 26.1.4, build 5650f9b
``` 
- Contruir contenedores
```bash
    docker-compose build
``` 
- Ejecutar contenedores
```bash
    docker-compose up
``` 

## ACERCA DE LA APP
* Backend patrón MVC (se refiere a modelo-vista-controlador en este caso se representa como: 
modelo = models, vista = routes, controlador = controller)
* Frontend patrón MVVM (se refiere a Modelo-vista-vistamodelo)
* La base de datos consta de dos modelos: 
- User: registro y autenticacion de usuarios 
- Event: Informacion basica para un evento. 
- Relación: uno a muchos, relacionando muchos eventos por cada usuario.  
* la Aplicacion permite el registro y la autenticacion de usuarios usando JWT y encriptacion SHA256 para la contraseñas. 
* La aplicacion permite crear, editar, eliminar y ver los eventos por cada usuario creado 
* Se debe especificar la ubicacion de la base de datos para la ejecicion de la aplicación. 

# Rutas
* Backend
```bash
    post 'auth/login', to: 'authentication#authenticate'
    post 'user/signup', to: 'users#create'
    get 'events/events', to: 'events#index'
    get 'events/event/:id', to: 'events#show'
    post 'events/create', to: 'events#create'
    put 'events/update/:id', to: 'events#update'
    delete 'events/delete/:id', to: 'events#destroy'
``` 
* Frontend
```bash
    home '/' 
    registro '/signup'
    contenido '/profile'
    crear '/create-event'
    editar /edit-event/:eventId'
``` 

## APP ESCALABLE
* Este ejercicio permite hacer la implementacion de nuevos modelos, implementacion de nuevos metodos y servicios, se puede ajustar las vistas y diseños segun las necesidades y contextos de uso. 

* Estructura de archivos principales:

```bash
lemonapp
│
├── lemonevent
│   ├── app
│   │   ├── controllers
│   │   │   ├── concerns
│   │   │   │   └──exception_handler.rb
│   │   │   ├──application_controller.rb
│   │   │   ├──authentication_controller.rb
│   │   │   ├──events_controller.rb
│   │   │   ├──users_controller.rb
│   │   │   ├──migrate.rb
│   │   │   ├──event.rb
│   │   │   ├──user.rb
│   │   ├── services
│   │   │   ├──authorize_api_request.rb
│   │   ├── config
│   │   │   ├──aplication.rb
│   │   │   ├──database.yml
│   │   │   ├──secrets.yml
│   │   ├── db
│   │   │   ├──migrate.rb
│   │   │   │   ├──create_users.rb
│   │   │   │   └──create_events.rb
│   │   │   ├──schema.rb
│   │   ├──lib
│   │   │  └──json_web_token.rb
│   ├──Dockerfile
│   ├──Gemfile
│   └──Gemfile.lock 
│
├── lemonfront
│   ├──src
│   │   ├──components
│   │   │  ├──CreateEvent.js
│   │   │  ├──EditEvent.js
│   │   │  ├──ErrorMessages.js
│   │   │  ├──EventForm.js
│   │   │  ├──Home.js
│   │   │  ├──Profile.js
│   │   │  └──RegisterForm.js
│   │   ├──utils
│   │   │  └──axiosConfig.js  
│   │   ├──App.css
│   │   ├──App.js
│   ├──Dockerfile
│   ├──package.json
│   └──package-lock.json
├──docker-compose.yml
└──README.md
```