# Every Simple Event System for Games
This event system is grab from my game written with Phaser game engine, Html/js/Vue and Typescript.
The reason this event system been used is that Vue and Phaser run on totally differnet rendering and update logic by themselves. So it's a good practice to separate the game logic layer with the html UI layer.

# Summery
It's a global system, can by notify and attach callbacks from anywhere.

# How to use
## First, create a new class. 
* Each event has its own class.
* The class contains a static manager and the actual event structure that you want to send through.
```javascript
export class EventHpChanged {
    public static Manager : EventManager<EventHpChanged> = new EventManager<EventHpChanged>();

    public hp : number;

    public constructor( _hp : number ) { 
        this.hp = _hp;
    }
} 
```

## Then attach callbacks
* This can be done anywhere in the code
```javascript
	EventHpChanged.Manager.attach( "hpupdate", ( evt : EventHpChanged ) => {
		console.log( evt.hp );
	})
```

## The callbacks will be called when notified:
* This also can be done anywhere in the code
```javascript
	EventHpChanged.Manager.notify( new EventHpChanged( hp) );
```


# Other notes
* You may use "detach" delete callbacks
* Different callbacks are idntified by their id parameters when attached.
