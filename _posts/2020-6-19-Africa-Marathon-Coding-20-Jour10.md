---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 10
---
Mes Solutions au Jour 10 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 10

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##   Problem A: Species 

### Sujet

![species]({{ site.baseurl }}/images/AMCC/animals.png)

Alicia has a huge garden which is the habitat of many animals that she really cares about. After  listening to a podcast about biodiversity, she becomes very concerned about the balance between species in her garden. She wants to know if there is a species that could overtake the others. In order to do so, she decides to carry out a census of all animals in the garden, writing down the species of each of them. Can you help her checking if there is strictly more animals from one species than the animals from all others species together?  

### Standard Input 

The input consists of the following lines: 
• on the first line: an integer N; 
• on each of the next N lines: the species of an animal as a string of length at most 20, containing only ASCII alphanumeric characters. 

## LIMITS

• 1 <= N <= 2 * 10^5

### Standard Output 

A string that appears a number of times that is greater than the sum of the others, if there is any, or the string “NONE” otherwise. 

![day10A]({{ site.baseurl }}/images/AMCC/day10ioA.png)

### Réflexion

Alicia a plusieurs animaux dans son jardin. Elle aimerait savoir s'il y a un équilibre entre les animaux de son jardin. Pour cela elle recense tous les animaux et on doit lui afficher le **nom** d'une espèce si sa population est plus grande que la population des autres espèces réunies s'il n'y en a pas, on affiche **"NONE"**.

Au début on nous donne le nombre **N** d'animaux dans le jardin puis la liste de tous les animaux.

Il nous revient donc de trouver l'effectif **E** de chaque espèce et vérifier si l'effectif **Emax** de l'espèce avec la plus grande population est plus grand que N/2.


### SOLUTION PYTHON 3:

```py

from collections import Counter

animals = []
n=int(input())

for _ in range(n): animals.append(input())


compteur = Counter(animals)
best = compteur.most_common(n)

print(best[0][0] if 2*best[0][1]>n else "NONE")


```

## Problem B: Charles 

### Sujet

![Ants]({{ site.baseurl }}/images/AMCC/ant.png)

Charles is fascinated by ants. In order to observe a colony of ants over a long period, Charles managed to build a program that uniquely identifies each ant, using image recognition. (Yes, every ant  is unique.) Inside the program, each ant is tagged with a unique nonnegative integer.  Whenever there is  a birth in the colony, the new ant is given a new tag, different from all tags already assigned. Whenever some ant disappears, its tag falls back into the pool of available tags.

Charles’s program works as follows. It first scans the whole colony, building the list of tags of the ants that are recognized. Then it assigns fresh tags to the new ants. To do so, the program simply picks the first natural number (i.e., nonnegative integer) that is not currently assigned to any ant, and so on. Due to some glitches in the image recognition device and in the program, there are sometimes negative or very large numbers that appear in the input list. These are simply ignored by Charles’s program.

Your job is to reimplement the part of Charles’s program that finds a fresh tag to assign to a new ant.

### Standard Input

The input consists of the following lines: 
    • on the first line: an integer N; 
    • on the next N lines: some integers X1, . . . , XN, one per line.  

## Limits 

The input satisfies 0 <= N <= 10^6. Each integer Xi has less than 100 digits

### Standard Output

The smallest natural number that does not belong to the set *{X1, . . . , XN }*.  
 
![ExampleDay10]({{ site.baseurl }}/images/AMCC/day10ioB.png)

### Réflexion

Charles veut observer une colonnie de fourmilles sur une longue période. Pour identifier chaque fourmille de la colonnie Charles a un programme qui assigne un numéro à chaque fourmille. Pour cela le programme scanne chaque fourmille et attibue le plus petit nombre supérieur à 0 qui n'est pas encore utilisé à la nouvelle fourmille.

Pour celà on va prendre n=0:

- si n n'est pas attribué alors on affiche n et on arrête le programme

- sinon on incrémente n de 1 et on vérifie la condition précédente


### SOLUTION PYTHON 3:

```py

ant=set()
for _ in range(int(input())): ant.add(int(input()))

i=0
while True:
    if not (i in ant):
        print(i)
        break
    i+=1

 

```


## Problem C: Climate 
### Sujet

![Bird]({{ site.baseurl }}/images/AMCC/area.png)

Tania is a marine biologist. Her goal is to measure the impact of climate change on the population of Macaroni penguins. As most species of penguins, Macaroni penguins live in the southern hemisphere, near Antarctica. Tania is primarily focused on the population of Macaroni penguins near the “Îles Nuageuses” (in English, “Cloudy Islands”).

During summer, the ice around the islands melt and the islands becomes too small to host all the birds. Some penguins live on the icebergs floating around. For her study, Tania needs to measure the area of those icebergs. 

Using satellite imagery and image recognition, Tania has obtained a map of the icebergs and your goal is to measure their area. The island studied by Tania is quite small and the Earth can locally be approximated as a flat surface. Tania’s map thus uses the usual 2D Cartesian coordinate system, and areas are computed in the usual manner. . For instance, a rectangle parallel to the axes defined by the equations ***x1 <= x <=  x2*** and ***y1 <=  y <=  y2*** has an area of ***(x2 - x1) x (y2 - y1)***.

In Tania’s representation, an iceberg is a polygon represented by its boundary. For each iceberg Tania has noted the sequence of points ***p1, . . . , pk*** defining the border of the iceberg. The various icebergs never touch each other and they never overlap. Furthermore the boundary ***p1, . . . , pk*** of an iceberg is always a “simple” polygon, i.e. no two segments in ***[p1; p2], . . . , [pk; p1]*** cross each other. 

### Standard Input

The input consists of the following lines: 

• on the first line, an integer N, describing the number of polygons; 

• then N blocks of lines follow, each describing a polygon and composed of: 
    
on the first line, an integer P, the number of points defining the polygon border,
         
on the next P lines, two space-separated integers x and y, the coordinates of each border point. 
 

## Limits 

• The number N of polygons is such that 1 <=  N <=  1 000.

• Each polygon is described by P points with 3 <= P <= 50.

• All coordinates are such that 0 <= x, y <= 10^6. 

### Standard Output

The output should contain a single integer: the total area rounded to the nearest integer below. In other words, the output should be a single line containing a single integer I such that the total area A of the polygons described in the input is comprised between I included and I + 1 excluded (I <= A < I + 1).   
 
![ExampleDay10]({{ site.baseurl }}/images/AMCC/day10ioC1.png)

![ExampleDay10]({{ site.baseurl }}/images/AMCC/day10ioC2.png)

### Réflexion

Pour cet exercice on doit calculer les aires de N polygones dans le plan à partir des coordonnées de leurs extrémités puis afficher la partie entière de la somme de ces aires.

Si un polygone simple (c'est-à-dire sans aucune intersection d'aucune paire quelconque de côtés, en dehors du sommet commun à deux côtés successifs) a n sommets qui sont les points

![points]({{ site.baseurl }}/images/AMCC/p.svg)

et si Pi a pour coordonnées (xi , yi) alors l'aire du polygone (considérée comme un nombre positif si les sommets sont ordonnés dans le sens trigonométrique et négatif dans le cas contraire) est donnée par :

![formule]({{ site.baseurl }}/images/AMCC/formule.svg)


### SOLUTION C++:

```cpp

#include <bits/stdc++.h>

using namespace std;
using str=string;

const int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";
const double pi = std::acos(-1);


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
#define be begin()
#define en end()
#define rbe rbegin()
#define ren rend()
#define findIn(x,y) find(all(x),y)



void solve()
{
    int T;
    cin>>T;
   double res=0.0;

    for_n(i,T)
    {
        int P;

        vec<pair<double,double>> points{};
        cin>>P;

        for_n(j,P)
        {
            double x,y;
            cin>>x>>y;

            points.pb(make_pair(x,y));
        }

         double aire;

         double total=0;

         for(int k=0; k<points.size()-1; k++)
         {
             total+=(points[k].first*points[k+1].second-points[k].second*points[k+1].first);
         }

         total+=points.back().first*points.front().second-points.back().second*points.front().first;

         aire=total/2;

        

        res+=fabs(aire);
    }

    

    

    printf("%d",(int)res);

   
    
}

int main()
{
    solve();
}
```

##    Problem D: Lunar year  

### Sujet

![Lunear]({{ site.baseurl }}/images/AMCC/lunear.png)

To celebrate the Lunar New Year of the Rat, Douglas decides to count the number of rats living in his area. It is impossible for him to find all rats, as they tend to be well hidden.  However,  on the first day  of the new year, Douglas manages to capture n1 rats, and marks each of them with an ear tag before releasing them. On the second day of the new year, Douglas captures n2 rats, and observes that n12 of them had been marked during the first day. Douglas is asking for your help to estimate the total number of rats in his area. Looking up in your statistics textbook, you propose using the Chapman estimator  Ñ , given by: 

![Formula]({{ site.baseurl }}/images/AMCC/Formula.png)


### Standard Input 

The input consists of a single line, with three space-separated integers: n1, n2, n12, in that order.   

### Standard Output 

The output should contain a single line with the single integer Ñ.

![day10D]({{ site.baseurl }}/images/AMCC/day10ioD.png)

### Réflexion

C'est la nouvelle année lunaire du rat! Douglas veut estimer le nombre de rats dans sa région pour cela, le premier jour de l'année il capture des rats qu'il marque **n1**, le jour 2 il répète l'opération et marque les rats par **n2**. Mais pour estimer les rats il se rend compte qu'il y a des rats qui sont marqués par **n12**. Il décide donc d'utiliser [l'estimation de Chapman](https://en.wikipedia.org/wiki/Mark_and_recapture) donnée ci-dessus.


### SOLUTION C++:

```cpp

#include <bits/stdc++.h>

using namespace std;
using str=string;

const int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";
const double pi = std::acos(-1);


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
#define be begin()
#define en end()
#define rbe rbegin()
#define ren rend()
#define findIn(x,y) find(all(x),y)



void solve()
{
    double n1, n2, n12;

    cin>>n1>>n2>>n12;

    cout<<(int)((n1+1)*(n2+1)/(n12+1)-1);
    
}

int main()
{
    solve();
}
```

Au jour 10, j'ai résolu 4 exercices sur 5, j'ai occupé la 3 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.
