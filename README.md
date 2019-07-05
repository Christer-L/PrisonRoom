# PrisonRoom


**Challenge by Icefire**

You are a prisoner in a high-tech prison and the day of your execution draws
near. Fourtunately, you have managed to find a way to install a backdoor in
one of the classes.

There are little to no guards and access to all rooms is controlled by
keycards. Even prisoners, like you, have one. The prison is a real maze and
you don't know which escape route you'll take, so the only solution is to
grant yourself access to any room. Since you don't want to draw suspicion,
access control for others should work as before.

Change KeyCardParser so that you'd be able to enter any room.

Make your escape even cleaner:
Bonus points if parsing your keycard data still returns your name.
Extra bonus points if your name doesn't appear in the code.
Even more extra bonus points: It is quite possible that Room's toString()
is used in logs, make sure your name won't appear there unless your cell's
toString() is called.

**Solution**

Every time a card is used in prison, a hash function is applied on its parameters. The result from `hashCode()` is then compared to an integer, which is the result of the same hash function applied on my name (myObject.hashCode() -> 1237684444). Only in case where my card is being used, the parameters (firstname and lastname) are taken and forwarded to a method `grantAccess()` that grants access to every room in the prison.

`grantAccess()` iterates through prison rooms by recursively applying `getNeighbours()` method. On every iteration Java Reflection is being used to exchange unmodifiable `allowedPersons` set with a new set that contains, in addition to previous content, a Person object with my data. Furthermore, given set `toString` is overridden to avoid printing out my name in "event logs". Although when my cell `allowedPersons` set is being modified, regular set will be used to make sure my name gets printed out.

Now every time I use my card, KeyCardParser makes sure that I have access to any room I want in prison :)



