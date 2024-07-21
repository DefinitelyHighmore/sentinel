# sentinel
A Library for watching containers using a LootTable trick
Download from releases and drop the ``.zip`` file directly into your datapacks folder

>[!Warning]
>May cause visual flickering of Items inside container.

>[!Important]
>* This datapack works for ``chest_minecart`` and ``hopper_minecart``
>* Pack can watch upto 65535 containers at once.

## Function Tags

### ``#senti:open``
* Run by the player when they open a watched container
* Entity may be targetted by the player using the following selector:

```mcfunction
execute as @e[type=senti:container,tag=senti.container,predicate=senti:target] ...
```

* Entity's Items are available at ``senti:api new``. You can make changes to this and use the Set Items function further below to edit contents open initial opening.




### ``#senti:changed``
* Run by the watched container that has had a change in contents
* Old contents in storage ``senti:api old``
* New contents in storage ``senti:api new``
* All players with the watched container open may be targetted by the following selector:

```mcfunction
execute as @a[predicate=senti:target] ...
```

### ``#senti:closed``
* Run by the player who closed a watched container
* Container can be targetted with the same predicate again


### ``#senti:fully_closed``
* Run by the container after all players have closed it.
* Players can be targetted with the same predicate



## Functions

### Initialize a container
Executing as the container, run the function below
```mcfunction
execute as <container> run function senti:api/watch
```

### Set Items in a container
>[!Important]
>***DO NOT*** directly edit items in the container, use this function
```mcfunction
# This should be invoked inside a function called by this pack's function tags, it will target the currently selected container.
# Input: data modify storage senti:api Items set value []
function senti:api/items
```

### Stop watching a container
Executing as the watched container, run the function below
```mcfunction
execute as <container> run function senti:api/stop_watching
```
