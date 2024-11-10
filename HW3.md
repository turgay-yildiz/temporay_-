# COGS 566 - Assignment 3

> **Credit:** [PROBMODS](https://probmods.org/)

## 1. Explaining Away (35)

Consider the Tug of War model that we discussed in the tutorial:

~~~~javascript
var model = function() {
  var strength = mem(function (person) {return Math.max(gaussian(1, 1), 0.01)})
  var lazy = function(person) {return flip(1/3) }
  var pulling = function(person) {
    return lazy(person) ? strength(person) / 2 : strength(person) }
  var totalPulling = function (team) {return sum(map(pulling, team))}
  var winner = function (team1, team2) {
    totalPulling(team1) > totalPulling(team2) ? team1 : team2 }
  var beat = function(team1,team2){_.isEqual(winner(team1,team2), team1)}

  condition(beat(['bob', 'mary'], ['tom', 'sue']))

  return strength('bob')
}

var dist = Infer({method: 'MCMC', kernel: 'MH', samples: 25000}, model)


print('Expected strength: ' + expectation(dist))
viz(dist)
~~~~

In this model, the posterior distribution for `strength('bob')` has an expected value of around 1.45. Bob is stronger than the average strength of 1. 

Find an example of *explaining away* that would cancel out initial belief that Bob is stronger than average? In other words, enter additional evidence that would cancel out the belief that Bob is stronger than average based on *explaining away* type of reasoning. Describe why this reasoning is *explaining away*.

Show *Expected strength* of Bob before and after entering this evidence.

## 2. Extending Tug of War model (65)

Extend the Tug of War model as follows: 
- People have two properties affecting their performance `strength` and `cleverness`. The outcome of most games probably depends on both properties, but some games may depend more on one than another. 
- Have two different games (e.g. tug of war and table tennis), these games depend differently on the two factors. 

~~~~
// your model here

~~~~

