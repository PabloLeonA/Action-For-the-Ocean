# Action-For-the-Ocean
Action for the ocean es un proyecto realizado para el hackathon de LaunchX que ayudara a la conservación de playas y oceanos de México.

# Controllers


# UserController

Aqui se crea el controler y se conecta con los servicios.

``` javascript
const UserBeachService = require("./../services/UserBeachService");

class UserBeachController {

    static createLocation(location){
        return UserBeachService.createLoacation(location);
    }

}

module.exports = UserBeachController;
```

# UserBeachController


Aqui se se crean y se conectan los servicios.

``` javascript
const UserService = require("./../services/UserService");

class UserController {

    static async register(user){
        return UserService.register(user);
    }

    static login(user){
        return UserService.login(user);
    }

    static updateUser(user){
        return UserService.updateUser(user);
    }

    static getUserData(user){
        return UserService.getUserData(user);
    }
}

module.exports = UserController;
```
