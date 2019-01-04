# Dice2Win Subgraph

This
[subgraph](https://github.com/graphprotocol/graph-node/blob/master/docs/getting-started.md)
analyzes the [dice2win](https://dice2.win/) smart contract and collects
some very simple statistics. For now, all it does is tally up the winnings
of players ('beneficiaries') and counts the number of times each player has
won the jackpot.

Dice2Win is a smart contract that allows players to bet on a number of
secure and random events, simulating, for example, rolling a die. The smart
contract emits events that reflect the winnings of players for each
bet. Our subgraph collects these events and keeps track of the total
winnings of each player.

## Query Example

This query will find all players that won the jackpot at least once. Just
copy and paste it into the dashboard of your
[graph-node instance](http://127.0.0.1:8000/subgraphs/name/dice2win)


```
    query lucky_duckies {
      beneficiaries(where: {jackpots_gt: 0}) {
        id
        winnings
        jackpots
      }
    }
```

This query will return the biggest winners:

```
    query whales {
      beneficiaries(first: 10, orderBy: winnings, orderDirection: desc) {
        id
        winnings
      }
    }
```
