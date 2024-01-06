# Spec

# Glossary
1. AVN: Animal Vs Npc is a game based on frames.
2. Unit: An entity in AVN, which has ATK, HP, Range and CD.
3. Troop: A list of Units that are teamed up under a battle.
4. Animal: A list of Units that can be place by player, animal can only stay at the position where it put. Animals have cost, player needs to spend eggs to summon them.
5. NPC: A list of Units that keep walking leftward or attacking animal. NPC has attribute speed, which means how fast does it move leftward
6. Attack: The attack mode of the Units, Unit will perform its Attack when it isn't in cooldown
7. Cooldown: After Attack, units need to wait for it's CD time then it can Attack again.
8. Skill: When the unit satisfy its skill condition, it will perform its unique skill.
9. Egg: Player can get an egg every 20 second (Have 2 at start), player spends eggs to create Animals.
10. Map: The Map is a 9x5 grids.
11. GoalLine: GoalLine is the left side of the leftest column of Map.
12. Win: if player defeats all the NPC in its round.
13. Lose: if NPC passes over the GoalLine



# Animal
- **Goose** (Bird)
    - <font color=red>ATK: 0</font>  <font color=green>HP: 200</font> <font color=orange>Range: 0</font> <font color=blue>CD: 10s</font> <font color=purple>Cost: 1</font>
    - Attack: Spawn an egg every 10 seconds. 
- **StupidBird** (Bird)
    - <font color=red>ATK: 25</font>  <font color=green>HP: 600</font> <font color=orange>Range: 1</font> <font color=blue>CD: 2s</font> <font color=purple>Cost: 1</font>
    - Attack: Attack the enemy nearby, cause the damage of its ATK.
    - Skill: When StupidBird get damaged to remain (400/200), StupidBird will fly to a random row leftmost spare space.
- **Squirrel** (Mammal)
    - <font color=red>ATK: 25</font>  <font color=green>HP: 100</font> <font color=orange>Range: 1</font> <font color=blue>CD: 0.5s</font> <font color=purple>Cost: 1</font>
    - Attack: Attack the enemy nearby, cause the damage of its ATK.
    - Skill: When Squirrel defeats an enemy, player will get additional two eggs.
- **Duck** (Bird)
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: inf</font> <font color=blue>CD: 2s</font> <font color=purple>Cost: 2</font>
    - Attack: Throw an egg to enemy, cause the damage of its ATK.
- **Monkey** (Mammal) 
    - <font color=red>ATK: 25</font>  <font color=green>HP: 200</font> <font color=orange>Range: 1</font> <font color=blue>CD: 2s</font> <font color=purple>Cost: 2</font>
    - Attack: Attack the enemy nearby, cause the damage of its ATK.
    - Skill: Monkey will put a bike behind it, the bike will be a component (HP:1000, ATK:0) 
- **LakeGoddness** (Mammal)
    - <font color=red>ATK: 100</font>  <font color=green>HP: 300</font> <font color=orange>Range: 1</font> <font color=blue>CD: 1s</font> <font color=purple>Cost: 3</font>
    - Attack: Attack the enemy nearby, cause the damage of its ATK.
    - Skill: When LakeGoddness defeat an enemy, all the animal around it (3x3, includes itself) will be healed 50 HP.
- **CSIEstudent** (Mammal)
    - <font color=red>ATK: 0</font>  <font color=green>HP: 1</font> <font color=orange>Range: 0</font> <font color=blue>CD: 1s</font> <font color=purple>Cost: 3</font>
    - Attack: CSIE student is so weak, he can't attack everything,
    - Skill: When CSIE student dies, all the enemy in current screen will stop moving. (Like petrochemical/petrofy in HW2)


# Npc
- **BirdHunter**
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: 3</font> <font color=blue>CD: 2</font> <font color=purple>Speed: 0.1</font>
    - Attack: Shoot an animal within its range and cause the damage of its ATK.
    - Skill: If BirdHunter's target is a Bird, he will cause extra 50 damage.
- **Missionary**
    - <font color=red>ATK: 50</font>  <font color=green>HP: 200</font> <font color=orange>Range: 1</font> <font color=blue>CD: 2</font> <font color=purple>Speed: 0.1</font>
    - Attack: Cause the damage of its ATK
    - Skill: The animal attacked by Missionary, whose CD will be doubled. (Can't trigger multiple times on the same target)

- **Customer**
    - <font color=red>ATK: 30</font>  <font color=green>HP: 200</font> <font color=orange>Range: 1</font> <font color=blue>CD: 1</font> <font color=purple>Speed: 0.5</font>
    - Attack: Cause the damage of its ATK
    - Skill: The animal who the Customer first meet will exchange its place with Customer. (Jump in line)
- **BikeDragger**
    - <font color=red>ATK: 30</font>  <font color=green>HP: 200</font> <font color=orange>Range: 1</font> <font color=blue>CD: 1</font> <font color=purple>Speed: 0.1</font>
    - Attack: Cause the damage of its ATK
    - Skill: If the target is a Bike, BikeDragger will defeated immidiately.
- **Driver**
    - <font color=red>ATK: 70</font>  <font color=green>HP: 600</font> <font color=orange>Range: 1</font> <font color=blue>CD: 5</font> <font color=purple>Speed: 0.5</font>
    - Attack: Cause the damage of its ATK
    - Skill: When Driver attack, all the animal in the same row will get damaged.
- **CampusSecurity**
    - <font color=red>ATK: 0</font>  <font color=green>HP: 1000</font> <font color=orange>Range: 1</font> <font color=blue>CD: inf</font> <font color=purple>Speed: 0.1</font>
    - Attack: CampusSecurity does nothing
    - Skill: They really do nothing, but can attract the fires of animal.