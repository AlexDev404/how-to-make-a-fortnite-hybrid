# How to make A Hybrid Server
## this is all just the most basic, you will not be able to get cloudstorage and profiles using this tutorial

- choose a programming language you are comfortable with, for this example i will be using python and nodejs
- create a web server, such as sanic for python and Express.js for nodejs projects
### express web server example
```
const express = require('express')
const app = express()
const port = 3000
app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```
### sanic webserver example
```
from sanic import Sanic
from sanic.response import text

app = Sanic("MyHelloWorldApp")

@app.get("/")
async def hello_world(request):
    return text("Hello, world.")

app.run(host="localhost", port=69)    
```
- after you have created a webserver you can move on to creating your endpoints!
- an endpoint is used for the fortnite client to send a request to the webserver, and the webserver returns the item the client is requesting

### sanic example
```
@app.route('/test')
async def test(request):
  return sanic.response.json({})
```
### express example
```
app.all('/test', (req, res) => {
  res.json([])
})
```
- in theese endpoitns you will need to return specific json data that the fortnite client wants all minimum required endpoints required with their response json will be linked below

| Required Endpoints | Json Data |
| ------ | ------ |
| /content/api/pages/fortnite-game | [https://fortnitecontent-website-prod07.ol.epicgames.com/content/api/pages/fortnite-game][json] |
| /content/api/pages/fortnite-game/media-events | [https://fortnitecontent-website-prod07.ol.epicgames.com][json] |
| /fortnite/api/game/v2/enabled_features | [https://fortnitecontent-website-prod07.ol.epicgames.com/fortnite/api/game/v2/enabled_features][json] |
| /fortnite/api/v2/versioncheck/<version> | [https://fortnitecontent-website-prod07.ol.epicgames.com/fortnite/api/v2/versioncheck/Windows][json] |
| /fortnite/api/calendar/v1/timeline | [https://fortnitecontent-website-prod07.ol.epicgames.com/fortnite/api/calendar/v1/timeline][json] |
| /socialban/api/public/v1/<accountId> | return with [] |
| /fortnite/api/storefront/v2/keychain | [https://api.nitestats.com/v1/epic/keychain][json] |



- once you have created all your endpoints you may now move on to the next step
- you will need to launch fortnite with arguments, or replace the anticheat files
- then inject a dll which redirects specific things from your fortnite client to your hybrid backend
- you shuold load into your hybrid server if you did everything correctly
