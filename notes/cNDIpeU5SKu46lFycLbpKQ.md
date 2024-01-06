# Report
[HOME PAGE](https://g0v.hackmd.io/HJ5OzxhXTGWGTxG4iMf6HA?both)
| Name | Student ID | 
| -------- | -------- | 
| 王靖傑     | b06902035     |
|沈韋辰 | B07902078|
| 張力文  | B05901191        |
| 吳宗翰| B06902003 |

## Contribution
### 王靖傑
- Design the architecture of this game
- Understand FXGL, and explain to teammates
- Implement the prototype animal & npc components
- Implement AnimalVsNpcApp and AnimalVsNpcFactory
- Implement collision handler 
### 沈韋辰
- Implement concrete components bases on the template
- Fix detail bugs
- Establish group pages and spec.
### 張力文
- Dealing with BirdHunter's animation and Makefile
### 吳宗翰
- Dealing animations


## Background
Once upon a time, there are so many animal live in Zui-Yue Lake at NTU. 

One day, a hunter came in and shoot our bird friend Goose! The Goose was dead and been taken over. From that day, more and more weird people came to NTU and start to invade this beautiful lake. Because every time they come, they do the same thing, kill the bird, harass the students, bla bla bla... animals give they a name --- NPC.

***"We must team up to defeated them!"*** said the duck.
***"But how can we win them? We're just tiny animals, NPCs are much stronger than us!"*** said the squirrel.

At this moment, a beautiful blue bird flies from somewhere to them.
***"Hi friends, my name is BlueBird, I know you guys are confused by the NPCs. I'm a magic bird come from NTU magic club, so I know how to help you."*** 

The BlueBird suddenly conjures a colorful egg, animals are shocked by this scene.
***"As long as you eat this magic egg, you will have super power to defeated the NPCs!"***

***"Let me try it!""*** The little yellow duck snatches the egg and eats it. Her body becomes larger, an egg emerge from her button and shots to the other side of the lake!

***"Me too! Me too!"*** After seeing the grow of the duck, animals can't wait to try this fantastic egg.

Now, all the animals live around Zui-Yue Lake have super power! Could they send the NPCs back home? Install our app ***"AVN: Zui-Yue Lake Defense Action"*** now!

## Game Flow
- At the beginning of the game, you will get two eggs as the cost to producing our units. It will cost eggs when producing the player's units.
- Each of our units (Animals) will have different skills, it could be an attack or laying eggs, etc.
- The enemy (NPC) will continue to attack you, and you need to produce units to stop the enemy from attacking.
- The enemy will attack from the right. When the enemy reaches the far left, the enemy wins, otherwise when the enemy is completely wiped out, the player win.


## UML


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a0ca87cf7a842f2ca7d45e54035d3bb.png)


## Design
### fxgl
- a java game engine based on javafx
- open sourced and contains fruitful APIs
### Glossary
1. AVN: Animal Vs Npc is a game based on frames.
2. Unit: An entity in AVN, which has ATK, HP, Range and CD.
3. Troop: A list of Units that are teamed up under a battle.
4. Animal: A list of Units that can be place by player, animal can only stay at the position where it put. Animals have cost, player needs to spend eggs to summon them.
5. NPC: A list of Units that keep walking leftward or attacking animal. NPC has attribute speed, which means how fast does it move leftward
6. Attack: The attack mode of the Units, Unit will perform its Attack when it isn't in cooldown
7. Cooldown: After Attack, units need to wait for it's CD time then it can Attack again.
8. Skill: When the unit satisfy its skill condition, it will perform its unique skill.
9. Egg: Player can get an egg every 20 second (Have 2 at start), player spends eggs to create Animals.
10. GoalLine: GoalLine is the left side of the leftest column of Map.
11. Win: if player defeats all the NPC in its round.
12. Lose: if NPC passes over the GoalLine
### Roles
#### Animals
- **Goose** (Bird)
    - <font color=red>ATK: 0</font>  <font color=green>HP: 200</font> <font color=orange>Range: 0</font> <font color=blue>CD: 10s</font> <font color=purple>Cost: 1</font>
    - Attack: Spawn an egg every 10 seconds. 
- **StupidBird** (Bird)
    - <font color=red>ATK: 25</font>  <font color=green>HP: 600</font> <font color=orange>Range: 1</font> <font color=blue>CD: 2s</font> <font color=purple>Cost: 1</font>
    - Attack: Attack the enemy nearby, cause the damage of its ATK.
    - Skill: When StupidBird get damaged to remain (400/200), StupidBird will fly to a random row leftmost spare space.
- **Duck** (Bird)
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: inf</font> <font color=blue>CD: 2s</font> <font color=purple>Cost: 2</font>
    - Attack: Throw an egg to enemy, cause the damage of its ATK.
#### Npc
- **BirdHunter**
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: 3</font> <font color=blue>CD: 2</font> <font color=purple>Speed: 0.1</font>
    - Attack: Shoot an animal within its range and cause the damage of its ATK.
    - Skill: If BirdHunter's target is a Bird, he will cause extra 50 damage.
- **Missionary**
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: 1</font> <font color=blue>CD: 2</font> <font color=purple>Speed: 0.1</font>
    - Attack: Cause the damage of its ATK
    - Skill: The animal attacked by Missionary, whose CD will be doubled. (Can't trigger multiple times on the same target)
## Classes
### AnimalVsNpcApp
- The entry point of this game
- Initiate all variables, control the flow of this game
- Setup the UI
- Spawn npc every 10 seconds
- Shut down the game when receving ```NpcReachGoalEvent```

### Entity
- Defined by fxgl
- The role that can be controlled by user input or by the game machanism
- Each entity can have multiple different ```Component```

### Component
- Defined by fxgl.
- Mainly used for controlling the entities or record the data of the entities.
- ```OnAdded()```: this method is called when the component is added to an entity
- ```onUpdate(double tps)```: this method is called for each frame, and input the time elapsed of this frame

### AnimalVsNpcFactory
- Spawn various kinds of entities
- Put ```@Spawns("name")``` in the head of the method
- When other class calls ```getGameWorld().spawn("name")```, it will invoke the method wrote in this class

### UnitComponent
- This is the super class of both AnimalComponent and NpcComponent
- This is a sub class of Component
- We store common properties of animal and npc to this class (e.g. ATK, HP, CD...)
- Initiate timer in ```onAdded()```
- Define ```performAttack()``` method, which is called every CD seconds
- ```changeHP()``` method can be called when other entities do something to it

### AnimalComponent
- Sub class of UnitComponent
- Store the cost of this animal

### BlueBirdComponent
- Override the ```performAttack``` method to spawn an egg

### DuckComponent
- Override the ```performAttack``` method to throw a duck egg towards npc

### StupidBirdComponent
- Special skill: when HP is less than (400/200), it will fly to the leftmost of a random row
- Override the ```changeHP()``` method so that it can fly away when HP is less than (400/200)

### NpcComponent
- Override the ```move()``` method, which is called by ```onUpdate()```
- ```setStop()```: when collude with animals or performing attack, the animal will stop moving


## Advantages of our design
- Using FXGL framework significantly reduce the development time of our project
- Adopting OCP to help our project more modulization and easy to debug
- Our game's background story is based on the actual events happening in NTU
## Disadvantages of our design
- We put too many contents into one component, instead, we can split each sub-task to one component (e.g. component that only deals with move())
## Other packages that we have used
- com.almasb.fxgl
- javafx

