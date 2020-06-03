---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 5
---
Mes Solutions au Jour 5 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 5

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem B: Vote 

### Sujet

Jenabkhan who has become billionaire from his Laboo bussiness, is now running for president. His country uses a strange mechanism, so-called electoral college, to select the president. There are several states in the country, and each state counts the votes independently. Depending on the population, each state has some members in the electoral college, and all of those members will vote the candidate with the majority of votes in their state. In the case of ties, each state has some tie-break rule to announce the clear winner. The president will be the candidate who receives more than half of votes in the electoral college.  
Given the chance of Jenabkhan to win in each state, compute his winning probability in the electoral college. 

### Standard Input 

The input consists of several test cases. Each test case starts with a line containing a single integer n denoting the number of states (1 ⩽ n ⩽ 1000).  Each of the next n lines contains a real value pi  with at most 4 digits after the decimal point (0 ⩽ pi ⩽ 1) and a positive integer ei, specifying the winning probability of Jenabkhan in the i-th state and the number of electoral votes associated with that state, respectively. The total number of members in the electoral college is an odd number and is no more than 2000. The input terminates with a line containing 0 which should not be processed.

### Standard Output 

For each test case, output in a single line containing the winning probability of Jenabkhan, rounded to exactly four digits after the decimal point (e.g., 0.3000 is correct while 0.3 is not). 

#### Sample Input

1

0.4 1

3

0.5 1

0.5 2

0.5 10

3

0.5 1

0.5 2

0.5 2 

2

0.2 1

0.8 10

2

0.25 1

0.751 10

0

#### Sample Output

0.4000

0.5000

0.5000

0.8000

0.7510

### Réflexion

Pour cet exercice, on a n Etat qui votent. Pour le ième Etat Jenabkhan a une probabilité p\[i] d'être élu pour e\[i] électeurs. On nous demande la probabilité que Jenabkhan a d'obtenir les votes de plus de la moitié des électeurs du pays.

Puisqu'il faut prendre certains Etats et d'autre non, alors il s'agit d'un [sac à dos 0-1](https://fr.wikipedia.org/wiki/Problème_du_sac_à_dos), la probabilité est la valeur et le poids est le prix.

Si le nombre total d'électeurs est N(impair)

Alors la probabilité recherchée est P(X>=[N/2])

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
#define be begin()
#define en end()
#define rbe rbegin()
#define ren rend()
#define findIn(x,y) find(all(x),y)
 

void solve()
{
    
    int N;
    
    while(true)
    {
        cin>>N;
        if(!N) return;
        vec<double> dp(2001,0);
        
        dp[0]=1;
        int voies= 0,compteur = 0;
        for_n(i,N)
        {
            int x;
            double p;
            cin>>p>>x;
            if(p == 1.0)
            {
                compteur += x;
                -- i;
                -- N;
                continue;
            }
            voies+= x;
            for_n(j,voies+1)    
                dp[j] *= 1-p;
            for(int j=voies; j>x-1; --j)    
                dp[j] += dp[j-x] * p / (1-p); 
        }
 
        double ans = 0;
        voies+= compteur + 1;
        for(int i= voies/2 ;i< voies+1; i++)    
            ans +=  dp[i-compteur];
        printf("%.4f\n", ans);
    }
    return ;
}


int main(){ solve();}

```


##  Problem D : Candy 

### Sujet

Pokemon  Go  just  released  the  Buddy  update.  It  lets  you  select  a  Pokemon  to  appear  alongside  your trainer's avatar on your profile screen. As you walk with your buddy, it will find candy that can be used to evolve the Pokemon.

The Buddy system divides the Pokemons into 3 groups. Each group gives one candy upon walking for 1, 3, and 5 kilometers respectively. 

In this problem you will be given the Pokemon group G, the number of candies C you initially have, and the number of candies E required to evolve the Pokemon. You should calculate the number of Kilometers required to walk in order to evolve the Pokemon.

### Standard Input

Your  program will be tested on one or more test cases. The first line of the input will be a single integer  T, the number of test cases (1 ≤ T ≤ 100). 
Each test case consists of a line containing three space separated integers: 

**G: The group of the Pokemon (1 ≤ G ≤ 3)** 

**C: The initial candies you have (0 ≤ C ≤ 100)** 

**E: The candies required to evolve the Pokemon (1 ≤ E ≤ 100)** 


### Standard Output

For each test case, print a single line containing the number of Kilometers of walking required to Evolve the Pokemon.


### Sample Input

2

1 15 51

1 18 21

#### Sample Output

36

3

### Réflexion

Dans le jeu, vous avez un pokemon et vous avez besoin d'un nombre **E** de bonbons pour le faire évoluer. Le pokemon gagne un bonbon sur un certain nombre **dG** de Km parcourrus en fonction du groupe auquel il appartient. Sachant que vous avez un nombre initial **C** de bonbons, il est demandé la distance à parcourrir pour faire évoluer votre pokemon.

La distance d a parcourrir est donc:

**d=(E-C)*dG** si C < E

**d=0** si C>=E

### SOLUTION C++:

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
#define be begin()
#define en end()
#define rbe rbegin()
#define ren rend()
#define findIn(x,y) find(all(x),y)



void solve()
{
    int N;
    cin>>N;
    while(N--)
    {

        int G,C,E;
        cin>>G>>C>>E;
        if(G==1 && C<E)
            cout<<E-C<<endl;
        else if(G==2 && C<E)
           cout<<(E-C)*3<<endl;
        else if(G== 3 && C<E)
        {
           cout<<(E-C)*5<<endl;
        }
        else
        {
            cout<<0<<endl;
        }
        
        
    }
}

int main()
{
    solve();
}

```


Au jour 5, j'ai résolu 2 exercices sur 5, j'ai occupé la 5 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












