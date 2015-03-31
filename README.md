# VideumCodeup Bomberman

Visit http://bomberman.videumcodeup.se/

Register your name here http://bit.ly/1CI9x2T

Your character will not be able to do anything, you'll have to write the code
that controls your character yourself.

Press `Ctrl+E` to open the editor. Press `Ctrl+S` to save and close the editor.

See the API below for learning what you can make your character do.

# API

This is the API for the server-side version of Bomberman. Written by [Andreas
Lundahl](https://github.com/andreaslundahl) and [Kevin
Sjöberg](https://github.com/kevinsjoberg).

## Commands

Commands are sent as [JSON](http://json.org/) over
[WebSockets](https://developer.mozilla.org/en-US/docs/WebSockets).

### start-movement

Request to start moving the Bomberman in the given direction.

**directions:** `"up", "down", "left", "right"`

```json
{"command": "start-movement", "arguments": ["up"]}
```

## stop-movement

Request to stop moving the Bomberman.

```json
{"command": "stop-movement", "arguments": []}
```

## place-bomb

Request to place a bomb at the tile of where the Bomberman stands.

```json
{"command": "place-bomb", "arguments": []}
```

## Stream

The stream from the server will contain transactions to the game state in the following form:

    [{"id":"some-id","coll":"some-collection","type":"add","value":{"some key": "some value"}]

This means that the value ```{"some key": "some value"}``` will be added to the collection `some-collection`, with the id ```some-id```.

Retractions look like this:

    [{"id":"some-id","coll":"some-collection","type":"retract"}]

However, the first message that will be sent from the server contains your player id, like this:

    {"id":"some-id"}
