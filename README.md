# mtg_deck_simulator
A very simple Magic: The Gathering cards deck simulator notebook for statistical purposes.

# Description
Deck preparation in the Magic The Gathering card game requires a good library of cards and serious strategical skills.
The different card types and their additional abilities must "play together" in order to defeat the opponent.
However, at the very basis of deck preparation, there is the need for balance in mana costs, i.e., the player must consider how much mana is needed to cast each spell and put together a deck that allows him or her to cast spells at any time.
This simulator provides a simple tool to estimate how balanced a deck is.
Given a deck, it plays regular rounds of the game and records the number of cards in hand and lands in the territory.
Rapid decks will estinguish a player's hand more rapidly.
Slower decks will show a larger number of cards in hand until later rounds.
This tool goes beyond simple estimates of deck balance that looks at the histogram of mana costs across cards.
Given the scarsity of Python based MTG engines and simulators, this project has enough reasons to exist in my humble opinion.
It can be extended in the future by including card types such as creatures, enchantments, etc. or mana producing cards using APIs and databases freely available from the web such as https://github.com/MagicTheGathering/mtg-sdk-python.
See below for more details.

# Features
- There is only one player.
- In mtg_sim, mana and cards are considered all colorless, i.e., only the combined mana cost is considered for each card and mana of any color is usable
- In mtg_sim_with_cards, colors are obtained with mtg-sdk and its online database to retrieve card info and cards can be played according to the available mana for each color, including colorless
- No card types such as creatures, sorceries, etc., are used except Lands.
- Cards are considered integers in mtg_sim and are always playable as long as there is enough lands of any type to cover the combined mana cost.
- Cards are colored cards but have no type (except Lands), they are always playable as long as there is enough mana to cover the cost for each color, including colorless (for a cost of 'X', 1 land is used)
- None of the round phases of the original game are considered except draw step, cast spell (play land and cast spell as part of the main phase), discard (cleanup step).
- Again, there's no combat phase, given there are no creatures.
- In mtg_sim, all the cards whose collective mana costs is lower or equal to the available mana are played, ordered by mana cost (i.e., no strategy).
- In mtg_sim_with_cards, only 1 random card is played among the cards whose cost can be covered with the available lands.
- For the cleanup step, a random card is discarded.
- In mtg_sim_with_cards, one random land is played in each turn.

# How to use it
Start a Jupyter notebook server and open the open the notebook.
It should be self explanatory.
Once the deck files are saved from mtg_sim_with_cards, you can skip the cells where the deck is loaded from csv since that usually takes few tens of seconds to query the web.
You can simply load the deck from the dck files with `deck.load`.

# For developers
One could easily extend the simulator by creating a `Card` object with all sorts of features and introduce game rules to determine whether cards can be played or not.
For now, I use only colors to correctly cover the mana costs.
Finding a strategy to play multiple cards is not trivial but given there aren't many cards in one's hand at any time, one could easily try all combinations and play the one with which the largest number of spells can be cast.
The card catalogue is retrieved from the available Magic: The Gathering API project https://docs.magicthegathering.io/ using the Python wrapper https://github.com/MagicTheGathering/mtg-sdk-python.
See the `load_csv_deck` notebook in which I load a deck file created with the Delver Lens app https://delverlab.com/.
I then used the same strategy in mtg_sim_with_cards to create decks, save them into .dck files and use them for rapid retrieval instead of querying the web every time.
The idea would be to retrieve the relevant information for each card from the database (e.g., cost and type) and introduce basic rules when casting spells.
For instance, an Enchant Creature cannot be cast if there are no creatures in the game.
I can see how this can be done I'm planning to introduce it in the code.
Ideally, one would also retrieve information about card abilities, such as mana producing cards, and a second player, and blablabla, however this is clearly out of the scope of this project and likely won't be ever introduced.

# Notes
This is the a Python based, open source, unofficial and certainly the most stupid MTG game engine I'm aware of.
This is certainly not a full blown MTG simulator (yet?).
For that, you may want to have a look at https://www.slightlymagic.net/wiki/List_of_MTG_Engines or simply search the GitHub.
Here is one interesting related project https://github.com/hlynurd/open-mtg.
Did you know that Google's DeepMind hasn't been able to develop a decent AI MTG player as of 2018?

# Acknowledgments
Magic: The Gathering is a registered trademark of Wizards of the Coast.
© 1995-2018 Wizards of the Coast LLC, a subsidiary of Hasbro, Inc. All Rights Reserved.
https://magic.wizards.com/en
I have no affiliation whatsoever with Wizards of the Coast LLC nor with Hasbro, Inc.
This code is released under the freest license there is.
In fact, I'm already annoyed by the fact there is my username on this repository.
