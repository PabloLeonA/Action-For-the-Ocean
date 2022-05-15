# Action-For-the-Ocean
Action for the ocean es un proyecto realizado para el hackathon de LaunchX que ayudara a la conservación de playas y oceanos de México.

# Routes

## Api Routes

Se crean la conexion de api para las routes:

``` javascript
const express = require("express");
const usersRoutes = require("./usersRoutes");
const usersBeach = require("./usersBeach");

function routerApi(app) {
    const router = express.Router();
    app.use("/api/v1", router);
    router.use("/users", usersRoutes);
    router.use("/usersBeach", usersBeach);
}

module.exports = routerApi;
```

## userBeach

Aqui se crea la conexion con controllers/UserBeachController en caso de que la conexion sea correcta nos arrojara 200 en caso de que no sea correcta nos arroja 400 y un mensaje de error.

``` javascript
const express = require("express");
const UserBeachController = require("./../controllers/UserBeachController");

const router = express.Router();

router.post("/", async (req, res) => {
    try {
        const userData = {
            userId: req.body.userId,
            beachId: req.body.beachId,
            latitude: req.body.latitude,
            longitude: req.body.longitude,
            rating: req.body.rating
        };
        const createLocation = await UserBeachController.createLocation(userData);
        return res.status(200).json({
            message: createLocation
        });
    } catch (error) {
        res.status(400).json({
            message: error.message,
        });
    }
});

module.exports = router;
```

## userRoutes
Aqui se crea la conexion con controllers/UserController una vez calidando el correo nos arroja 200 si es correcto y sino un 400 y un mensaje de error

``` javascript
const express = require("express");
const UserController = require("../controllers/UserController");

const router = express.Router();

router.post("/", async (req, res) => {
    try {
        const userData = {
            email: req.body.email,
            password: req.body.password,
        };
        const login = await UserController.login(userData);
        return res.status(200).json({
            message:login
        });
    } catch (error) {
        res.status(404).json({
            message: error.message,
        });
    }
});

router.post("/register", async (req, res) => {
    try {
        const userData = {
            name: req.body.name,
            lastname: req.body.lastname,
            email: req.body.email,
            password: req.body.password,
            country: req.body.country
        };
        const register = await UserController.register(userData);
        return res.status(200).json({
            message: register
        });
    } catch (error) {
        res.status(400).json({
            message: error.message,
        });
    }
});

router.post("/update" , async (req , res) => {
    try {
        const userData = {
            email: req.body.email,
            password: req.body.password,
        };
        const userInfo = await UserController.getUserData(userData);
        return res.status(200).json({
            message: userInfo
        });
    } catch (error) {
        res.status(404).json({
            message: error.message,
        });
    }
});

router.put("/update", async (req, res) => {
    try {
        const userData = {
            name: req.body.name,
            lastname: req.body.lastname,
            email: req.body.email,
            password: req.body.password,
            country: req.body.country
        };
        const update = await UserController.updateUser(userData);
        return res.status(200).json({
            message: update
        });
    } catch (error) {
        res.status(400).json({
            message: error.message,
        });
    }
});

module.exports = router;
```



