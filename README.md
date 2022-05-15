# Action-For-the-Ocean
Action for the ocean es un proyecto realizado para el hackathon de LaunchX que ayudara a la conservación de playas y oceanos de México.

# Routes

## Api Routes

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
``` javascript

