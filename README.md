# PrisonRoomSolution

Every time a card is used in prison, a hash function is applied on its parameters. The result from `hashCode()` is then compared with an integer, which is the result of the same hash function applied on my name (myObject.hashCode() -> 1237684444). Only in case where my card is being used, the parameters (firstname and lastname) are taken and forwarded to a method `grantAccess()` that grants access to every room in the prison.

`grantAccess()` iterates through prison rooms by recursively applying `getNeighbours()` method. On every iteration Java Reflection is being used to exchange unmodifiable `allowedPersons` set with a new set that contains in addition to previous content a Person object with my data. Furthermore, given set `toString` is overridden to avoid printing out my name in "event logs". Although when my cell `allowedPersons` set is being modified, regular set will be used to make sure my name gets printed out.

Every time I use my card KeyCardParser makes sure that I have access to any room I want in prison.


Development of solution finished: March 23, 2019
Writing the description finished: March 29, 2019


