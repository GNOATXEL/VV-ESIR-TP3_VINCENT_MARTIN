# Test the Date class

Implement a class `Date` with the interface shown below:

```java
class Date implements Comparable<Date> {

    public Date(int day, int month, int year) { ... }

    public static boolean isValidDate(int day, int month, int year) { ... }

    public static boolean isLeapYear(int year) { ... }

    public Date nextDate() { ... }

    public Date previousDate { ... }

    public int compareTo(Date other) { ... }

}
```

The constructor throws an exception if the three given integers do not form a valid date.

`isValidDate` returns `true` if the three integers form a valid year, otherwise `false`.

`isLeapYear` says if the given integer is a leap year.

`nextDate` returns a new `Date` instance representing the date of the following day.

`previousDate` returns a new `Date` instance representing the date of the previous day.

`compareTo` follows the `Comparable` convention:

* `date.compareTo(other)` returns a positive integer if `date` is posterior to `other`
* `date.compareTo(other)` returns a negative integer if `date` is anterior to `other`
* `date.compareTo(other)` returns `0` if `date` and `other` represent the same date.
* the method throws a `NullPointerException` if `other` is `null` 

Design and implement a test suite for this `Date` class.
You may use the test cases discussed in classes as a starting point. 
Also, feel free to add any extra method you may need to the `Date` class.


Use the following steps to design the test suite:

1. With the help of *Input Space Partitioning* design a set of initial test inputs for each method. Write below the characteristics and blocks you identified for each method. Specify which characteristics are common to more than one method.
2. Evaluate the statement coverage of the test cases designed in the previous step. If needed, add new test cases to increase the coverage. Describe below what you did in this step.
3. If you have in your code any predicate that uses more than two boolean operators check if the test cases written to far satisfy *Base Choice Coverage*. If needed add new test cases. Describe below how you evaluated the logic coverage and the new test cases you added.
4. Use PIT to evaluate the test suite you have so far. Describe below the mutation score and the live mutants. Add new test cases or refactor the existing ones to achieve a high mutation score.

Use the project in [tp3-date](../code/tp3-date) to complete this exercise.

## Answer

### 1.

#### Caractéristiques et blocs

`isValidDate(int day, int month, int year)`

##### Caractéristiques :

Année :
Normalement toujours valide.

Mois :
Mois valide (ex. : 1, 6, 12) ;
Mois invalide (ex. : 0, 13)

Jour :
Jour valide pour le mois (ex. : 1, 15, 28) ;
Jour invalide pour le mois (ex. : 0, 32)

Année bissextile :
Année bissextile (février a 29 jours) ;
Année non bissextile

##### Blocs :

Mois valide, jour valide ;
Mois invalide, jour valide ;
Mois valide, jour invalide ;
Mois invalide, jour invalide ;

`isLeapYear(int year)`

##### Caractéristiques :

Année :
Année bissextile ;
Année non bissextile ;

##### Blocs :

Année bissextile ;
Année non bissextile

`nextDate()`

##### Caractéristiques :

Date actuelle :
Date au milieu du mois ;
Dernier jour du mois ;
Scénarios d'année bissextile et non bissextile ;

##### Blocs :

Milieu du mois, non dernier jour ;
Milieu du mois, dernier jour ;
Février dans une année bissextile ;
Février dans une année non bissextile ;
Fin des mois (sauf février) dans une année non bissextile ;
Fin des mois (sauf février) dans une année bissextile ;

`previousDate()`

##### Caractéristiques :

Date actuelle :
Date au milieu du mois ;
Premier jour du mois ;
Scénarios d'année bissextile et non bissextile

##### Blocs :

Milieu du mois, non premier jour ;
Milieu du mois, premier jour ;
Février dans une année bissextile ;
Février dans une année non bissextile ;
Début des mois (sauf février) dans une année non bissextile ;
Début des mois (sauf février) dans une année bissextile ;

`compareTo(Date other)`

##### Caractéristiques :

Comparaison des dates :
Date avant l'autre ;
Date après l'autre ;
Date identique à l'autre ;

##### Blocs :

Date avant l'autre ;
Date après l'autre ;
Date identique à l'autre ;

#### Caractéristiques communes à plusieurs méthodes :

Année : Année bissextile, année non bissextile

Mois : Mois valide, mois invalide

Jour : Jour valide, jour invalide


