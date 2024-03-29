## Some documentation for the json elements the card files can contain:


### name
The name of the card as a string. Must be UNIQUE! If missing or empty the card won't be loaded. This is the only strictly mandatory element.

### desc
A string explaining what the card does to the player. The default is an empty string.

### type
The type of the card as a string. The original game supports:
- "Landmark"
- "Primary Industry"
- "Secondary Industry"
- "Restaurants"
- "Major Establishment"
Custom types can be added. When a player has build all "Landmarks" the player wins. "Restaurants" are executed first, "Major Establishment" last and all others in between. The default is "Secondary Industry".

### icon
The icon of the card as a string. The original game supports:
- "tower"
- "wheat"
- "cow"
- "gear"
- "bread"
- "factory"
- "fruit"
- "cup"
- "boat"
- "suitcase"
Custom icons can be added. These must not contain whitespaces. Whitespaces will be removed. Every player can only own every "tower" card once. "tower" cards can't be swaped, moved or get renovated. Cannot be empty. The default is bread.

### activation_no
A list of numbers for which dice rolls the card gets activated. Should be empty for "Landmarks". The default is an empty list and as such won't be activated.

### activation
A string indicating which players can activate the card. Possible are only:
- "passive"
- "self"
- "others"
- "all"
For "Landmarks" "passive" should be used and is their fallback. For "Primary Industry" the fallback is "all", "others" for "Restaurants". Other types will fallback to "self" which also is the default.

### cost
The amount of money needed to buy this card as in int. The default is 1.

### start
How many of these cards every player gets at the start of the game as an int. Usually will be 0 for most cards and 1 for some cards. The default is 0. Has to be 1 or 0 for "tower" cards.

### available
A float that is multiplied with the amount of players to specify how many of these cards are available to buy. The default is 2. For "tower" cards this will be overwritten with 1. The starting cards do not count to this limit except for "tower" cards.

### actions
A machine readable list of strings which specify what actions will be executed by this card.  Possible options (WIP):
- GET int|"inv": Player receives int coins from the bank
- LOSE int|"inv"|"all": Loses the specified amount
- STEAL int|"inv"|"all": Steals the specified amount from the active player
- COMBO str int: Player gets int coins for each card with str icon
- RENOVATE: Sets this card to renovating
- GRANT str: Grants some functionality to the player. Will be executed upon obtaining if activation == "passive"
- REVOKE str: Revokes some functionality from the player if available. Will be executed upon obtaining if activation == "passive"

### investable
An integer indicating the maximum investment that can be made at the end of a turn. 0 will disable investments. Default is 0.
