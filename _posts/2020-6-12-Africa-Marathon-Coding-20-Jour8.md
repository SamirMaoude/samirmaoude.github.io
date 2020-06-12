---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 8
---
Mes Solutions au Jour 8 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 8

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem A: Luanda 

### Sujet

Luanda municipality has set up a new charging method for the Congestion Charging Zone (CCZ) which controls the passage of vehicles in Luanda’s high-congestion areas in the congestion period (CP) from 6:30 to 19:00. There are plate detection cameras inside or at the entrances of the CCZ recording vehicles seen at the CCZ. The table below summarizes the new charging method. 
 
![Luanda]({{ site.baseurl }}/images/AMCC/luanda.png)
 
Note that the first time and the last time that a vehicle is seen in the CP may be the same. Write a program to compute the amount of charge of a given vehicle in a specific day. 

### Standard Input 

The first line of the input contains a positive integer n (1 ⩽ n ⩽ 100) where n is the number of records for a vehicle. Each of the next n lines contains a time at which the vehicle is seen. Each time is of form \<hour\>:\<minute\>, where \<hour\> is an integer number between 0 and 23 (inclusive) and \<minute\> is formatted as an exactly two-digit number between 00 and 59 (inclusive).

### Standard Output 

Print the charge to be paid by the owner of the vehicle in the output. 

![Example]({{ site.baseurl }}/images/AMCC/ioA.png)

### Réflexion

La municipalité de Luanda a ouvert une station de péage et chaque véhicule doit payer un montant en fonction de la première fois et de la dernière fois qu'il a été vu au cours des heures d'ouverture de la station.

On nous donne les heures (**h:m**) au cours desquelles un véhicule a été repéré par les caméras et on doit déterminer le montant qu'il doit solder.

Les heures d'ouvertures de la station sont **6:30 à 19:00**

Pour taiter les heures, nous allons les convertir en minutes donc 6h-30 fait 6\*60+30=390 et 19h-00 fait 19\*60+0=1140

Nous allons maintenant rechercher la première fois et la dernière fois que le véhicule a été vu entre 390 et 1140

Pour cela on va stocker les heures qui respectent la condition ci dessous dans un tableau qu'on nommera **seen**

**CONDITION: 390>= h*60+m <=1140**

Si à la fin seen ne contient rien alors le véhicule payera 0

Sinon la première fois **P** que le véhicule a été vu est le plus petit élément de seen et la dernière fois **D** est le plus grand élément de seen

Il suffit de regarder alors quelle ligne correspond à **P** et **D** dans le tableau précédent et afficher le montant.


## SOLUTION C++:
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
    vec<int> seen{};
    int T;
    cin>>T;
    while(T--)
    {
        
        int h;
        int m;

        scanf("%d:%d", &h,&m);


        h = h * 60 + m;
        if(h >= 390 && h <= 1140)
        {
            seen.pb(h);
           
        }
    }
    if(!seen.size())
        cout<<"0";
    else
    {
        sort(all(seen));
        if(seen.front() >= 390 && seen.front() <= 600 && seen.back() >= 390 && seen.back() <= 960)
            cout<<"24000";
        else if(seen.front() >= 390 && seen.front() <= 600 && seen.back() >= 961 && seen.back() <= 1140)
            cout<<"36000";
        else if(seen.front() >= 601 && seen.front() <= 960 && seen.back() >= 601 && seen.back() <= 960)
            cout<<"16800";
        else if(seen.front() >= 601 && seen.front() <= 1140 && seen.back() >= 961 && seen.back() <= 1140)
            cout<<"24000";
    }

}

int main()
{
    solve();
}

```


## Problem B: ACPC 

### Sujet

The African ChamPions Cup (ACPC), the most prestigious football league in Africa, is reaching its end, and people are eagerly waiting for the finals, which happened to be between the two most popular African teams, Zamalek and Mazembe. 
 
The ACPC finals consist of two matches, with each team competing as the home team in one match. The winning team is determined by aggregate score, the sum of the scores of the two matches. For example, if the scores of the two matches are Zamalek 6–0 Mazembe in the first match, and Mazembe 3–1 Zamalek in the second match, then the aggregate score will be Zamalek 7–3 Mazembe, meaning that Zamalek is the winner. If aggregates are equal, the away goals rule is used to determine the winner, in which case the winner is the team that scored the most goals in the match it played away from home. If the result is still equal, a penalty shootout is required. 
 
Augusto, an avid football fan, is trying to figure out various scenarios in which her favorite team wins the finals. To this end, he aims to write a program that gets as input the number of goals in the two matches, and decides which team is the winner if it can be derived from the aggregate scores and the away goals rule, otherwise declares that the match goes to penalty kicks. You are going to help Augusto write such a program. 

### Standard Input

The first line of the input contains two space-separated integers p1 and s1, where p1 and s1 are the number of goals scored by Zamalek and Mazembe, respectively, in the first match in which Zamalek is the home team. The second line contains two space-separated integers s2 and p2, where s2 and p2 are the number of goals scored by Mazembe and Zamalek, respectively, in the second match in which Mazembe is the home team. All input integers are between 0 and 20, inclusively. 

### Standard Output

In the output, print the name of the winning team, either Zamalek or Mazembe, if the winner can be determined by the aggregate scores and the away goals rule. Otherwise, print Penalty.
 
![Example]({{ site.baseurl }}/images/AMCC/ioB.png)

### Réflexion

Là les footeux comme moi vont adorer ce problème. Il s'agit de déterminer après un match allé-retour entre Zamaleck et Mazembe qui sera qualifié ou s'il doit y avoir une séance de pénaltys pour les départager.

Sachant que le match allé se joue à Zamaleck, on nous donne les scores sous cette forme:

**Score allé: a b**

**Score retour: c d**

On déduit déjà que Zamaleck a marqué a+d buts et Mazembe a marqué b+c buts

-Si a+d > b+d alors **Zamaleck est le vainqueur**

-Si a+d < b+d alors **Mazembe est le vainqueur**

-Si a+d = b+d alors il faut regarder les buts marqués à l'extérieur par chacun deux

Dans ce cas:

-Si d > b alors **Zamaleck est le vainqueur**

-Si d < b alors **Mazembe est le vainqueur**

Si d = b alors **Il faut des Pénaltys pour les départager**


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
    int a,b,c,d;
    cin>>a>>b>>c>>d;

    if(a+d>b+c) cout<<"Zamalek"<<endl;
    
    else if(b+c>a+d) cout<<"Mazembe"<<endl;
    
    else
    {
        if(b>d)
            cout<<"Mazembe"<<endl;
        else if(b<d)
            cout<<"Zamalek"<<endl;
        else
        {
            cout<<"Penalty"<<endl;
        }
        

    }
    
    
}

int main()
{
    solve();
}

```

## Problem C: MarathonChallenge

### Sujet

MarathonChallenge is a gathering event at Mapcom similar to TGIF events at Google. Some entertainment programs like pantomime, foosball, Xbox/PS4, and several board games are part of the event. You are going to set up a dart game in MarathonChallenge. As a techie organizing a game for techies, you would rather use a smart screen and write a program to calculate the scores instead of hanging a traditional dartboard and scoring the shots manually. Your program must get the coordinates of dart shots for a player and calculate his/her total score. The score for each dart shot (at point (x, y)) is calculated based on its distance from the center of the dartboard (point (0, 0)). If the distance is d millimeters, the score is calculated based on the following table: 

![Cible]({{ site.baseurl }}/images/AMCC/cible.png)

### Standard Input

The first line of the input contains a single integer N  as the number of dart shots for a player (1  ⩽  N  ⩽  100).  Each  of the next N lines contains two space-separated integers as the coordinates (x, y) of a dart shot. The coordinates are in millimeters and their absolute values will not be greater than 300.  

### Standard Output

Print a single line containing the total score of the player. 
 
![Example]({{ site.baseurl }}/images/AMCC/ioC.png)

### Réflexion

C'est un jeu de Tir à l'arc et pour chaque flèche tirée un score est attribué en fonction de la distance entre l'origine de la cible et la position (x,y) de la flèche sur la cible.

Il faut donc calculer cette distance **d= (x²+y²)^0.5**

Le score d'un joueur est la somme de tous les points équivalents à chaque d.


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
    int res=0;

    while(T--)
    {
        int x,y;
        cin>>x>>y;
        double d=sqrt(x*x+y*y);

        

        if(d<=10)
        {
            res+=10;
            continue;
        }
        else if(10<d && d<=30)
        {
            res+=9;
            continue;
        }
        else if(30<d && d<=50)
        {
            res+=8;
            continue;
        }
        else if(50<d && d<=70)
        {
            res+=7;
            continue;
        }
        else if(70<d && d<=90)
        {
            res+=6;
            continue;
        }
        else if(90<d && d<=110)
        {
            res+=5;
            continue;
        }
        else if(110<d && d<=130)
        {
            res+=4;
            continue;
        }
        else if(130<d && d<=150)
        {
            res+=3;
            continue;
        }
        else if(150<d && d<=170)
        {
            res+=2;
            continue;
        }
        else if(170<d && d<=190)
        {
            res+=1;
            continue;
        }
        else if(190<d)
        {
            res+=0;
            continue;
        }


    }

    cout<<res;
    
}

int main()
{
    solve();
}

```


Au jour 8, j'ai résolu 3 exercices sur 5, j'ai occupé la 5 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












