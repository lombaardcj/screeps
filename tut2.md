
### create a upgrader
```
Game.spawns['Spawn1'].spawnCreep( [WORK, CARRY, MOVE], 'Upgrader1' );
```

### create roles
```
Game.creeps['Harvester1'].memory.role = 'harvester';
Game.creeps['Upgrader1'].memory.role = 'upgrader';
```
### create upgrader module

```
var roleUpgrader = {

    /** @param {Creep} creep **/
    run: function(creep) {
	    if(creep.store[RESOURCE_ENERGY] == 0) {
            var sources = creep.room.find(FIND_SOURCES);
            if(creep.harvest(sources[0]) == ERR_NOT_IN_RANGE) {
                creep.moveTo(sources[0]);
            }
        }
        else {
            if(creep.upgradeController(creep.room.controller) == ERR_NOT_IN_RANGE) {
                creep.moveTo(creep.room.controller);
            }
        }
	}
};

module.exports = roleUpgrader;
```


# Add more harvesters
## create a upgrader
```
Game.spawns['Spawn1'].spawnCreep( [WORK, CARRY, MOVE], 'Upgrader2' );
```
```
Game.spawns['Spawn1'].spawnCreep( [WORK, CARRY, MOVE], 'Upgrader3' );
```
```
Game.spawns['Spawn1'].spawnCreep( [WORK, CARRY, MOVE], 'Upgrader4' );
```
```
Game.spawns['Spawn1'].spawnCreep( [WORK, CARRY, MOVE], 'Upgrader5' );
```



### add upgrader roles
```
Game.creeps['Upgrader2'].memory.role = 'upgrader';
```
```
Game.creeps['Upgrader3'].memory.role = 'upgrader';
```
```
Game.creeps['Upgrader4'].memory.role = 'upgrader';
```
```
Game.creeps['Upgrader5'].memory.role = 'upgrader';
```



