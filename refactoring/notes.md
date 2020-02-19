Refactoring notes
=================

2020-02-12
----------
* Extract compound conditionals into private methods (`cond1 && cond2`)
* Extract implicit conditionals into explicit methods (try to keep methods short (1 line) and don't that don't any params)
* When about to use 3 conditional branches, try to extract into a new object that handles those conditionals and to answer the conditionals

2020-02-18
----------
* Refactoring is the process of changing a software system in such a way that it does not alter the external behavior of the code yet improves
the internal structure
* Refactoring does not add new behavior, it improves the existing structure. It's a precise process that alters code via tiny steps and
carefully transforms one design into another
* Well-designed code is easy to change, refactoring is how you change from one design to the next, and tests allow you to refactor without punishment
* An object with many private methods exudes the design smell of having too many responsibilities. If your object has so many private methods that
you dare not leave them untested, consider extracting the methods into a new object.
* The extracted methods form the core of the responsibilites of the new object and so make up its public interface, which is (theoretically)
stable and thus safe to depend upon
