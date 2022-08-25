# Welcome to clash of bits!
This playground is an example of what a basic AI can be.

# Structure
One simple way to think about an AI for clash of bits to do those 3 things in descending order of priority :
- Survive
- Kill enemies in range
- Find an enemy to kill

# Code
Starting with the [python starter AI](https://github.com/Butanium/Clash-of-bits/tree/master/starterAIs/starter.py) building such an AI is simple. 
After collecting all the data, we can code our AI to adopt this behavior as follow : 
```py
    for ally_bot in ally_bots:
        closest_enemy = ally_bot.get_closest_enemy()
        if ally_bot.shield == 0:
            # The shield is empty, run for your life !
            ally_bot.flee(closest_enemy)
        elif closest_enemy.viewed_by(ally_bot).range_from_bot < 3:
            # The closest enemy can be attacked, let's destroy it
            ally_bot.attack(closest_enemy)
        else:
            # The closest enemy is too far away (we can't hit it), let's move closer
            ally_bot.move(ally_bot.get_closest_enemy())
    
    print(orders)
```
