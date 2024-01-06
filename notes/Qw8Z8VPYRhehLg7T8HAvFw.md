# Design Report

> Please follow the instructions in homework 1 (officially announced version on NTU COOL) to finish the report.

## Software Design

> The purpose of the design report is to help the TAs grade the software design (and bonus) part by
> human. We hope that you can illustrate every class of your design with:
>
> - its name
> - a **one-sentence** description of its duty
> - a **short** description of how it possibly interacts with other classes

> Don't elaborate too much on every class
> since we will directly inspect your code for details.

- Card
- Pattern
- Deck
- Player
- Gameflow

### Card implements Comparable<Card>
Card is the basic element to compose the class **Pattern** , and I use the interface Comparable to make it more powerful.
- attribute
    - **String suit**: Suit of the card.
    - **String rank**: Rank of the card.
    - **int weight**: helpful in comparing and sorting, obtained by above.
- public method
    - **Card(String str)**: Constructor
    - **int getWeight()**: For external class to get the weight.
    - **int compareTo(Card c)**: Cards can compare to each other make it easy to sort.
    - **String show()**: Return the formal string type to help output formatting. 
- private method
    - **int suitToInt(String suit)**: Helpful for the constuctor.
    - **int rankToInt(String rank)**: Same as above
    
    
### Pattern
Pattern consists of cards, its "type" can be very useful in other class.

- attribute
    - **enum ptype**: has SINGLE, PAIR, STRAIGHT, FULLHOUSE, PASS and ILLEGAL
    - **List<Integer> cardList**: Use weight to record cards in it.
    - **int card_N**: Number of cards in it.
    - **ptype type**: The pattern type of the instance.
- static method
    - **String typeToString(ptype pt)**: Turn type into string for output formatting.
- public method
    - **Pattern(List<Integer> weights)**: Constructor.
    - **ptype getType()**: Return the type of instance.
    - **int rank()**: Return the weight to represent how big is this pattern
- private method
    - **ptype checkType**: Helpful for the constuctor.
    - **boolean isStraight()**: Helpful for the constuctor.
    - **boolean isFullhouse()**: Helpful for the constuctor.
    
### Deck
This class is used to record what pattern is playing now, how big it is and how many player has passed. It's useful to determine whether cuurrent action of a player is illegal.
- static attribute
    - **Pattern.ptype state**: What kind of pattern is played now.
    - **int passed**: How many player has passed.
    - **int maxWeight**: Next player should play a pattern bigger than this one.
    - **boolean newRound**: When three players all pass.
- static method
    - **boolean available(Pattern cur)**: Return true if this pattern is available in current condition
    - **void checkNewRound**: Just to check if it is new round
    
### Player
This class define the behavior of a player.
- attribute
    - **String name**: Player's name
    - **List<Card> holding**: The cards the player holds.
    - **int holding_n**: Number of card the player holds.
    - **String msg**: Some messege can be read by other class.
- public method
    - **Player(String name)**: Constructor
    - **void ReceiveCard(String str)**: Useful when we deal the cards to players
    - **String getName()**: Return player's name
    - **String msg()**: Return some output message
    - **String ShowHolding()**: Show all the cards on the player's hand to help output
    - **boolean HasCard(Card T)**: Check if this player has a specified card, used to decide who first
    - **boolean isWin()**: Check if this player is won
    - **boolean play(String ins)**: Return true if the ins is legal, and remove the cards in holding
- private method
    - **Pattern GetCardsFromIndex(String ins)**: Help play() to get the card.
    - **String idToString(List<Integer> index)**: Help play() to get the formatted output.

### GameFlow
This class is used to control the flow of game, interact with players.

- static attribute
    - **List<Player> player_list**: List of the 4 players.
    - **int turn**: Record now is whose turn.
- public static method: 
    - **void GameInit(String deckString, List<String> playerNames)**: Register players' names, deal the card and decide the first player.
    - **void UpdateTurn()**: Turn to the next player
    - **Player GetCurrentPlayer()**: Get the reference of current player
- private static method: 
    - **int whoFirst()**: Find who has the club of 3
    
### Architecture
Main -> GameFlow, Desk -> Player -> Pattern -> Card
    
## Bonus Design: Open-Closed Principle (OCP)

> You will either get 0 or 20 points on this bonus.
> If you can't achieve it, don't report anything here.
