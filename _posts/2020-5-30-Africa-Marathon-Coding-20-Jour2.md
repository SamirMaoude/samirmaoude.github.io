---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 2
---
Mes Solutions au Jour 2 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 2

Il faut rappeler que chaque jour, une série de 5 exercices était donnés et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

## Problem A : Bicycle 

### Sujet
Most bicycle speedometers work by using a Hall Effect sensor fastened to the front fork of the bicycle.  A magnet is attached to one of the spokes on the front wheel so that it will line up with the Hall Effect switch once per revolution of the wheel.  The speedometer monitors the sensor to count wheel revolutions.  If the diameter of the wheel is known, the distance traveled can be easily be calculated if you know how many revolutions the wheel has made.  In addition, if the time it takes to complete the revolutions is known, the average speed can also be calculated. For this problem, you will write a program to determine the total distance traveled (in miles) and the average speed (in Miles Per Hour) given the wheel diameter, the number of revolutions and the total time of the trip.  You can assume that the front wheel never leaves the ground, and there is no slipping or skidding. 

### Standard Input 
Input consists of multiple datasets, one per line, of the form:

*diameter revolutions time*

The diameter is expressed in inches as a floating point value. The revolutions is an integer value. The time is expressed in seconds as a floating point value. Input ends when the value of revolutions is 0 (zero). 

### Standard Output 
For each data set, print:

**Trip #N: distance MPH** 

Of course N should be replaced by the data set number, distance by the total distance in miles (accurate to 2 decimal places) and MPH by the speed in miles per hour (accurate to 2 decimal places). Your program should not generate any output for the ending case when revolutions is 0.

### Constants 

For p use the value: 3.1415927.

There are 5280 feet in a mile. 

There are 12 inches in a foot. 

There are 60 minutes in an hour. 

There are 60 seconds in a minute. 

There are 201.168 meters in a furlong. 

#### Sample Input

26  1000  5

27.25  873234  3000

26  0  1000 

#### Sample Output

**Trip #1: 1.29  928.20**

**Trip #2: 1179.86  1415.84**


### Réflexion

Il s'agit de trouver la distance parcourue par le cycliste en Miles puis la moyenne de distance parcourue en MPH.

Puisque le diamètre de la piste est en inches, il faut la convertir en miles:

D'après les constantes du sujet, on a:

***12 inches ---> 1 foot***

***1 mile ---> 5280 feet***

On déduit donc que: ***1 mile ---> 5280\*12 inches***

Notre cycliste parcourt en réalité le pourtour du cercle R fois.

La distance voulue est donc **distance= D\*pi\*R** (en inches).

Il ne reste plus qu'à la convertir en miles.

Sachant désormais ***1 mile ---> 5280\*12 inches***, en appliquant la règle de trois a notre distance, on établit:

**distance= D\*pi\*R/(5280\*12)**

Maintenant il nous reste à trouver la moyenne de distance parcourue en heure avec le temps(TS) exprimé en secondes:

On a 1h ---> 3600 secondes donc notre temps en heure(TH) fait TH= TS/3600.

il ne reste plus qu'à diviser la distance par TH pour trouver la moyenne recherchée.

## SOLUTION C++:
```cpp
#include <bits/stdc++.h>

using namespace std;
using str=string;

const int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";

#define pii pair<int,int>
#define psi pair<str, int>
#define pis pair<int, str>
#define msi map<str, int>
#define mis map<int, str>
#define vec vector
#define ll long long
#define ull unsigned long long


#define for_n(i,n) for(int i=0; i<n; ++i)
#define pb(x) push_back(x)
#define ins(x) insert(x)
#define all(x) x.begin(),x.end()
#define findIn(x,y) find(all(x),y)


void solve()
{
    for(int i=1; i>0; i++)
    {
        double D, R, S;
        cin>>D>>R>>S;
        const double p=3.1415927;

        if(R==0)
            return;

        double dist=(D*p*R)/12/5280;

        printf("Trip #%d: %.2lf %.2lf\n",i,dist,dist*3600/S);
    }
}

int main()
{
    solve();
}

```

Pas si évident en fin de compte. Ah cet exercice, on s'en souviendra longtemps.

## Problem B: Binary numbers 

### Sujet

Adding binary numbers is a very simple task, and very similar to the longhand addition of decimal numbers.  As with decimal numbers, you start by adding the bits (digits) one column at a time, from right to left.  Unlike decimal addition, there is little to memorize in the way of rules for the addition of binary bits:

![binary]({{ site.baseurl }}/images/AMCC/bin.png)

### Standard Input

The first line of input contains an integer N, (1 <= N <= 1000), which is the number of binary addition problems that follow.   Each problem appears on a single line containing two binary values separated by a single space character.  The maximum length of each binary value is 80 bits (binary digits).  Note: The maximum length result could be 81 bits (binary digits). 


### Standard Output

For each binary addition problem, print the problem number, a space, and the binary result of the addition.  Extra leading zeroes must be omitted.


### Sample Input

3

1001101 10010

1001001 11001

1000111 1010110

#### Sample Output

1 1011111

2 1100010

3 10011101

### Réflexion

On nous fournit deux nombres binaires et il faut faire leur somme en base 2.

Une des solutions est de convertir les deux nombres en base 10 puis faire leur somme en base 10, convertir le résultat en base 2 et l'afficher.

Cette fois je vais utiliser python 3 car il possède déjà des fonctions pour effectuer ses opérations, ce qui me permettra d'aller plus vite. Vous pouvez quand même vous exerçer à coder ses fonctions dans votre langage préféré.

### SOLUTION PYTHON 3:

```python
    for i in range (1,int(input())+1):

        x,y=input().split()

        print(i,bin(int('0b'+x, 2) + int('0b'+y , 2))[2:])
```

Malheureusement au cours de l'épreuve je n'ai pas résolu ce problème car en voulant aller plus vite je n'ai pas lu l'énnoncé, juste la forme des input et output(ne faites pas comme moi haha) et il se trouve qu'il y avait une erreur de formatage.

Les inputs étaient formatés comme ça:

3  1001101 10010 1001001

11001 1000111 1010110

Ce qui a fait que je récupérais mal les entrées. Encore une fois, ne faîtes pas comme moi, lisez toujours les énnoncés.

## Problem C : Change 

### Sujet

J.P. Flathead’s Grocery Store hires cheap labor to man the checkout stations. The people he hires (usually high school kids) often make mistakes making change for the customers. Flathead, who’s a bit of a tightwad, figures he loses more money from these mistakes than he makes; that is, the employees tend to give more change to the customers than they should get. 

Flathead wants you to write a program that calculates the number of quarters ($0.25), dimes ($0.10), nickels ($0.05) and pennies ($0.01) that the customer should get back. Flathead always wants to give the customer’s change in coins if the amount due back is $5.00 or under. He also wants to give the customers back the smallest total number of coins. For example, if the change due back is $1.24, the customer should receive 4 quarters, 2 dimes, 0 nickels, and 4 pennies. 

### Standard Input 

The first line of input contains an integer N which is the number of datasets that follow. Each dataset consists of a single line containing a single integer which is the change due in cents, C, (1 ≤C ≤ 500). 

### Standard Output

For each dataset, print out the dataset number, a space, and the string: Q QUARTER(S), D DIME(S), n NICKEL(S), P PENNY(S) Where Q is he number of quarters, D is the number of dimes, n is the number of nickels and P is the number of pennies. 

#### Sample Input
3

124

25

194 

#### Sample Output

1 4 QUARTER(S), 2 DIME(S), 0 NICKEL(S), 4 PENNY(S)

2 1 QUARTER(S), 0 DIME(S), 0 NICKEL(S), 0 PENNY(S)

3 7 QUARTER(S), 1 DIME(S), 1 NICKEL(S), 4 PENNY(S) 

### Réflexion

Pour cet exercice il faut trouver le nombre minimum de pieces de quarter, dime, de nickel et de penny pour monnayer une somme C exprimée en centimes de dollar.

C étant en centime, nous allons aussi convertir les pieces disponibles en centimes. On a donc:

**1 QUARTER = 25 cents**

**1 DIME = 10 cents**

**1 NICKEL = 5 cents**

**1 PENNY = 1 cent**

Le nombre minimum de pieces est la somme du nombre minimum de chaque piece qu'il faut utiliser

Le nombre minimum de chaque piece est obtenu en faisant la division entière de C par sa valeur

Mais pour minimiser le résultat il faut commencer par chercher le résultat de la piece avec la plus grande valeur et à chaque fois soustraire de C ce résultat multiplié par la valeur de la piece

Pour trouver le minimum de quarter par exemple, on fait:

min(Q)=[C/25] puis on soustrait à C min(Q)*25 (Ce qui revient à C mod(25))

Ensuite on répète l'opération avec les autres pieces avec l'ordre de priorité qui est décroissant

## SOLUTION C++:
```cpp
#include <bits/stdc++.h>

using namespace std;
using str=string;

const int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";

#define pii pair<int,int>
#define psi pair<str, int>
#define pis pair<int, str>
#define msi map<str, int>
#define mis map<int, str>
#define vec vector
#define ll long long
#define ull unsigned long long


#define for_n(i,n) for(int i=0; i<n; ++i)
#define pb(x) push_back(x)
#define ins(x) insert(x)
#define all(x) x.begin(),x.end()
#define findIn(x,y) find(all(x),y)



void solve()
{
    int T;
    cin >>T;
    for_n(i,T){
        int C;

        cin>>C;

        

        int q=C/25; C%=25;
        int d=C/10; C%=10;
        int n=C/5; C%=5;

        printf("%d %d QUARTER(S), %d DIME(S), %d NICKEL(S), %d PENNY(S)\n",i+1,q,d,n,C);
    }


    


}

int main()
{
    solve();
}
```

Certains auront peut être reconnu le [problème du rendu de monnaie](https://fr.wikipedia.org/wiki/Problème_du_rendu_de_monnaie) et peuvent utiliser la programmation dynamique pour résoudre ce problème.

Malheureusement encore je n'ai pas résolu ce problème, entre temps j'avais une coupure d'électricité et j'avais plus de battérie(décidement ce jour 2).

## Problem D : The fastest road to banikoara  

### Sujet

![banikoara]({{ site.baseurl }}/images/AMCC/banikoara.png)

### Standard Input 

The first line of input contains a single integer P, (1 ≤ P ≤ 1000), which is the number of data sets that follow. Each data set begins with a line containing the number N of the remaining lines in the dataset (1 ≤ N ≤ 500), followed by a space, followed by the name of a departure town, followed by a space, followed by the name of a destination town. Each of these N lines contains a name of a departure town, followed by a space, followed by a name of a destination town, followed by the distance (in kilometers) between the two towns. The distance will be an integer and the name of town will be a string formed with characters [a-z] [A-Z] and with the sign “-”.  

### Standard Output

For each data set, you must generate a single output line containing the name of a town A and a space, followed by the name of town B, followed by a space, followed by the shortest distance to travel between towns A and B. 

#### Sample Input
1

4

Dassa-Zoume Banikoara

Dassa-Zoume Djougou 270

Banikoara Djougou 211

Parakou Banikoara 284 

Parakou Dassa-Zoume 225 

#### Sample Output

Dassa-Zoume Banikoara 481 

### Réflexion

Ici j'ai utilisé l'algorithme de [Dijkstra](https://fr.wikipedia.org/wiki/Algorithme_de_Dijkstra) que je vous invite à aller voir si, vous ne le connaissez pas. C'est un algorithme qui permet de trouver le plus court chemin pour relier deux sommets d'un graphe.

## SOLUTION C++:

```cpp
#include <bits/stdc++.h>

using namespace std;
using str=string;

const int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";

#define pii pair<int,int>
#define psi pair<str, int>
#define pis pair<int, str>
#define msi map<str, int>
#define mis map<int, str>
#define vec vector
#define ll long long
#define ull unsigned long long


#define for_n(i,n) for(int i=0; i<n; ++i)
#define pb(x) push_back(x)
#define ins(x) insert(x)
#define all(x) x.begin(),x.end()
#define b begin()
#define e end()
#define findIn(x,y) find(all(x),y)



typedef struct Ville {
    str name;
    int distance;
    Ville(const str &s, const int &d): name(s), distance(d) {}
} Ville;

bool operator < (const Ville &n, const Ville &o)
{
    return o.distance < n.distance;
}


void solve()
{
    int n, p;
    string debut, fin;
    msi subtree;
    map<string, vector<Ville>> carte;
    vector<Ville> queue;

    cin >> p;
    for_n(i,p) 
    {
        cin >> n >> debut >> fin;

        for_n(j,n)  {
           string debut, fin;
           int d;
           cin >> debut >> fin >> d;
           carte[debut].emplace_back(fin, d);
           carte[fin].emplace_back(debut, d);
           
        }

        queue.emplace_back(debut, 0);
        while (!queue.empty()) {
            make_heap(queue.rbegin(), queue.rend(), less<Ville>());

        Ville u = queue.back();

        queue.pop_back();
            if (subtree.find(u.name) == subtree.end()) {
                for (const auto &v : carte[u.name]) {
                    if (subtree.find(v.name) == subtree.end()) {
                        queue.emplace_back(v.name, u.distance + v.distance);
                    }
                }
                subtree.insert(make_pair(u.name, u.distance));
            }
        }
        cout << debut << " " << fin << " " << subtree[fin] << endl;

        carte.clear();
        subtree.clear();
    }

}

int main()
{
    solve();
}

```

Au jour 2, j'ai résolu 2 exercices, ce qui m'a valu la 11 place du classement final.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












