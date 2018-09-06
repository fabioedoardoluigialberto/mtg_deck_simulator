# mtg_deck_simulator
A very simple Magic: The Gathering cards deck simulator notebook for statistical purposes.

# Description
Deck preparation in the Magic The Gathering card game requires a good library of cards and serious strategical skills.
The different card types and their additional abilities must "play together" in order to defeat the opponent.
However, at the very basis of deck preparation, there is the need for balance in mana costs, i.e., the player must consider how much mana is needed to cast each spell and put together a deck that allows him or her to cast spells at any time.
This simulator provides a simple tool to estimate how balanced a deck is.
Given the number of lands in the deck as well as cards with mana cost of 1, 2, 3 and so on, it plays regular rounds of the game using a shuffled deck and records the number of cards played, lands in the territory and discarded cards.
Rapid decks will results in quickly emptying a player's hand.
Slower decks will show a larger number of cards in hand until later rounds.
This tool goes beyond simple estimates of deck balance by looking at the histogram of mana costs.
Given the scarsity of Python based MTG engines and simulators, this project has enough reasons to exist in my humble opinion.
It can be extended in the future by including card types such as creatures, enchantments, etc. or mana producing cards using APIs and databases freely available from the web such as https://github.com/MagicTheGathering/mtg-sdk-python.


# How to use it
Start a Jupyter notebook server and open the open the notebook.
It should be self explanatory.
Given the scarsity of Python based MTG engines and simulators, this project has enough reasons to exist in my humble opinion.
It can be extended in the future by including card types such as creatures, enchantments, etc. or mana producing cards using APIs and databases freely (?) available from the web.

# Features
- There is only one player.
- Mana and cards are considered colorless.
- There are no card types such as creatures, sorceries, etc., except Lands, cards are just integers representing mana cost (Lands are 0-cost cards).
- There are no combats, given there are no creatures.
- None of the steps of the original game are considered except draw step, cast spell (part of the main phase), discard (cleanup step).
- All the cards whose collective mana costs is lower or equal to the available mana are played, ordered by mana cost (i.e., no strategy).
- A random card is discarded if a card has to be discarded.

# For developers
For now, cards are just int numbers.
One could easily extend the simulator by creating a `Card` object with all sorts of features and introduce game rules to determine whether cards can be played or not.
The card catalogue can be retrieved from the available Magic: The Gathering API project https://docs.magicthegathering.io/ using the Python wrapper https://github.com/MagicTheGathering/mtg-sdk-python.

# Notes
This is the a Python based, open source, unofficial and certainly the most stupid MTG game engine I'm aware of.
This is certainly not a full blown MTG simulator (yet?).
For that, you may want to have a look at https://www.slightlymagic.net/wiki/List_of_MTG_Engines or simply search the GitHub.
Here is one interesting related project https://github.com/hlynurd/open-mtg.

# Acknowledgments
Magic: The Gathering is a registered trademark of Wizards of the Coast.
© 1995-2018 Wizards of the Coast LLC, a subsidiary of Hasbro, Inc. All Rights Reserved.
https://magic.wizards.com/en
I have no affiliation whatsoever with Wizards of the Coast LLC nor with Hasbro, Inc.
This code is released under the freest license there is.
In fact, I'm already annoyed by the fact there is my username on this repository.
