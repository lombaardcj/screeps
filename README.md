# screeps

### Step 1 Create harvester creep
```
Game.spawns['Spawn1'].spawnCreep([WORK,CARRY,MOVE], 'Harvester1');
```

### Step 2 Harvest in loop until full
```
module.exports.loop = function () {
    var creep = Game.creeps['Harvester1'];
    var sources = creep.room.find(FIND_SOURCES);
    if(creep.harvest(sources[0]) == ERR_NOT_IN_RANGE) {
        creep.moveTo(sources[0]);
    }
}
```

### Step 3 Harvest and return to spawn
```
module.exports.loop = function () {
    var creep = Game.creeps['Harvester1'];

    if(creep.store.getFreeCapacity() > 0) {
        var sources = creep.room.find(FIND_SOURCES);
        if(creep.harvest(sources[0]) == ERR_NOT_IN_RANGE) {
            creep.moveTo(sources[0]);
        }
    }
    else {
        if( creep.transfer(Game.spawns['Spawn1'], RESOURCE_ENERGY) == ERR_NOT_IN_RANGE ) {
            creep.moveTo(Game.spawns['Spawn1']);
        }
    }
}
```
