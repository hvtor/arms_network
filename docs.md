# Docs
This document describes the API available to you for this project.

## Objects

### `City`
The `City` object describes the various cities your agent can travel to. It has the following members:

#### Properties
##### `City.name`
The `name` of the `City`

##### `City.items`
An `Array` of `Item`s which describe the items available to each `City`

### `Item`
An `Item` in the game which can be bought and sold.

#### Properties
##### `Item.name`
The `name` of the `Item`

##### `Item.minPrice` and `Item.maxPrice`
These numbers determine the range at which the `Item.currentPrice` will evaluate to.

##### `Item.currentPrice`
The current price of the `Item`. If the `Agent` were to sell or buy the `Item` it would be at this cost.

#### Methods
##### `Item.recalculatePrice()`
Recalculates the `Item`s price when called.

### `Agent`
Represents the player of the game, this is the user profile.

#### Properties
##### `Agent.name`
The `name` of the `Agent`

##### `Agent.money`
This is how much cash on hand you have. When this gets to 0 you lose.

##### `Agent.inventory`
The `Agent`s inventory (`AgentInventory`) which contains all the `Item`s
the `Agent` is currently carrying.

#### Methods
##### `Agent.getRank()`
This method will return a `String` based on the Agent's current rank.

### `AgentInventory`
This is the `Agent`s inventory. It contains `AgentInventoryItem`s

#### Properties
##### `AgentInventory.inventory`
An `Array` which contains all the `AgentInventoryItem`s in an `Agent`s
inventory.

#### Methods
##### `AgentInventory.pop(item, quantity)`
Returns the `AgentInventoryItem` give by item. If the quantity becomes zero, 
it is removed from the `Agent`s inventory

##### `AgentInventory.push(item, quantity)`
Adds the `Item` with given `quantity` to the `Agent`s inventory. If the `Agent`
already has the item in their inventory, the `quantity` will be added to the inventory.

##### `AgentInventory.findItem(item)`
Returns the `AgentInventoryItem` for a given `Item`.


### `AgentInventoryItem`
This is an `Item` that exists in the `Agent`s inventory.
#### Properties
##### `AgentInventoryItem.item`
The `Item` in the `Agent`'s inventory.

##### `AgentInventoryItem.quantity`
The amount of `Item`s in the inventory.

### `Game`
This is the main object that manages the actual `Game`.

#### Properties
##### `Game.agent`
The `Agent` for this `Game`

##### `Game.cities`
A list of all the `Cities` available to travel to.
 
##### `Game.currentCity`
The `City` where the `Agent` is currently residing

#### Methods
##### `Game.buyingItem(item)`
This method is fired when the user clicks on the buy button.

`item`: The `Item` the user is trying to buy.

##### `Game.sellingItem(inventoryItem)`
This method is fired when the user clicks on the sell button. 

`inventoryItem`: The `AgentInventoryItem` the user is trying to sell.

##### `Game.changeCity(newCity)`
This method is fired when the user attemps to change city.

`newCity`: The `City` that the user is trying to change to.

##### `Game.refreshViews()`
Updates the UI of the game.