# sentinel
A Library for watching containers using a LootTable trick
Download from releases and drop the ``.zip`` file directly into your datapacks folder

>[!Warning]
>May cause visual flickering of Items inside container.

>[!Important]
>* This datapack works for ``chest_minecart`` and ``hopper_minecart``
>* Pack can watch upto 65535 containers at once.

## Function Tags

### ``#senti:viewer/open``
* Run by the player when they open a watched container
* The UUID of opened container (in string form) is present in storage ``senti:api uuid`` during this function tag call, use a macro to reference it.


### ``#senti:container/changed``
* Run by open watched containers that have a change in their contents
* Contents of previous tick in storage ``senti:api old``
* All players with the watched container open may be targetted by the tag ``senti.viewer`` during this function call

### ``#senti:container/tick``
* Run by all Open watched containers every tick
* All players with the watched container open may be targetted by the tag ``senti.viewer`` during this function call.
* This runs after ``#senti:container/changed`` in case a change happens.


### ``#senti:viewer/closed``
* Run by the player who closed a watched container
* Container can be targetted with the same predicate again


### ``#senti:fully_closed``
* Run by the container after all players have closed it.

### ``#senti:log_out``
* Run by the server when it detects a player logging out while having a container open.
* Player's name available during this function call at storage ``senti:api player.name``
* Player's UUID (int form) available during this function call at storage ``senti:api player.uuid``

### ``#senti:relog``
* Run by players, who logged out while having a container open, upon joining back.

## Functions

### Start Watching a container
Executing as the container, run the function below
```mcfunction
execute as <container> run function senti:start
```

### Stop Watching a container
Executing as the watched container, run the function below
```mcfunction
execute as <container> run function senti:stop
```
> [!Important]
> Please use the stop watching function when you want to get rid of a container, so that it's ID can be recycled.
