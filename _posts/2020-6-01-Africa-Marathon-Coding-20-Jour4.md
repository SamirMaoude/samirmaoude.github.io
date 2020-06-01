---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 4
---
Mes Solutions au Jour 4 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 4

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##   Problem A : Income

### Sujet

The amount of income tax imposed on any taxpayer depends on his/her income. For an income less than or equal to 1,000,000 Nairas, no tax is paid. For an income greater than 1,000,000 and less than or equal to 5,000,000 Nairas, the tax is 10% of the income. For an income over 5,000,000 Nairas, the tax is 20% of the income. You should write a program to calculate the net income of any given employee after the deducted tax. 

### Standard Input 

There are multiple lines in the input. Each line contains an employee’s income before the tax, which is a positive integer, a multiple of 1000, and not greater than 10,000,000. The input terminates with a line containing 0 which should not be processed.

### Standard Output 

For each employee, output a line containing the net income after the deducted tax

#### Sample Input

10000

50000

2000000

7500000

0 

#### Sample Output

10000

50000

1800000

6000000

### Réflexion

Ici il faut trouver les revenus d'une personne après qu'elle ait payé des taxes. Les taxes sont en fonction du revenu initial:

**0 si revenu <= 1000000**

**10% du revenu si 1000000< revenu <= 5000000**

**20% du revenu si le revenu est plus grand que 5000000**

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
    while(true)
    {
        int x;
        cin>>x;

        if(!x) return;

        if(x<=1000000) cout<<x<<endl;

        else if(x>1000000 &&x<=5000000) cout<<(int)(x-(x*10)/100)<<endl;

        else cout<<(x-(x*20)/100)<<endl;
        
        
    }
}

int main()
{
    solve();
}

```


## Problem B: Hassan

### Sujet

![binary]({{ site.baseurl }}/images/AMCC/key.png)

### Standard Input

There are multiple test cases in the input. The first line of each test case contains two spaceseparated integers m as the number of cuts in the customer’s key (1 ⩽ m ⩽ 10), and n as the number of keys with the same number of cuts in the trash-box (1 ⩽ n ⩽ 100). The second line of the test case consists of m space-separated integers, as the depths of cuts in the customer’s key. Each of the next n lines also contains m integers, as the depths of cuts in a trash-box key. The depth of cuts in each of these n + 1 keys are 1-digit positive integers given in the left-toright order. The input terminates with a line containing 0 0 which should not be processed. 


### Standard Output

For each test case, print a single line containing the number of keys in the trash-box that either match the customer’s key or can be cut to match it. 


### Sample Input

4 1

3 2 1 3

2 2 1 2

4 1

4 2 2 2

3 2 2 3

5 3

2 2 4 2 2

2 3 4 3 2

1 1 3 2 2

2 2 2 2 2

0 0
#### Sample Output
1

0

2

### Réflexion

Hassan est un fabricant de clefs et il arrive que des clients viennent commander des copies de clefs. Pour cela le client fournit le nombre de dents de sa clef et la profondeur de l'espace entre chaque dents. Il se trouve que Hassane dispose déjà d'un certain nombre de clefs avec ce nombre de dents et il aimerait savoir le nombre de clefs qu'il pourrait réutiliser parmi celles-ci pour confectionner la clef copie du client.

Une clef est réutilisable si la profondeur de l'espace entre une dent **d'indice i et la dent d'indice i+1** est inférieure ou égale à la profondeur de l'espace correspondant sur la clef du client. 

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
    while(true)
    {
        vec<int> depht{};
        int m,n;
        cin>>m>>n;
        if(!m) return;
        for_n(j,m)
        {
            int x;
            cin>>x;
            depht.pb(x);

        }
        int res=0;
        for_n(j,n)
        {
            bool ok=1;
            for_n(k,m)
            {
                int x;
                cin>>x;
                if(x>depht[k])
                {
                    ok=0;
                }

            }

            if(ok) res++;
        }

        cout<<res<<endl;
    }
}

int main()
{
    solve();
}

```


##  Problem C : Logo  

### Sujet

In order to design a logo, the organizing committee of the competition decided to publicly call for logos. It was not surprising that many logos were received in a short time as the young generation is actively taking part in any event. In the first round, logos were judged by some professional graphic designers, and the best logos being artistically capable to be the choosen logo were selected to be judged in the second round. 

The selected logos are now presented to the organizing-committee members for voting. The voting system is a little bit complicated: each member can vote for at most three different logos in some order. The first, second and third choices of each member are awarded 3, 2 and 1 points, respectively. The score of a logo is the total points the logo receives from all members. The logo with the highest score is the winner. In the case of ties, the winner is the logo with higher number of first votes. Again, if some logos have the same score and first votes, the logo with more second votes is the winner. If we still have ties, all of them would be winners. Given the voting information, your job is to identify the winner logo (or logos). 

### Standard Input 

There are multiple test cases in the input. The first line of each test case contains a positive integer n denoting the number of voters (1 ⩽ n ⩽ 100). Each of the next n lines starts with an integer di, representing the number of logos chosen by the i-th voter (1 ⩽ di ⩽ 3), followed by di different logo IDs showing the choices of that voter (from left to right). Each logo ID is a positive integer not exceeding 106. All integers in a line are separated with a single space. The input terminates with a line containing 0 which should not be processed. 

### Standard Output

For each test case, output a line containing the winner logos in the increasing order of their IDs. Logo IDs in a line must be separated with a single space. 

#### Sample Input

4

3 5 2 1

3 12 5 2

2 1 2

3 2 1 5

2

3 3 2 1

3 2 3 1

0 

#### Sample Output

2

2 3

### Réflexion

Pendant un concours de logos, on veut désigner le meilleur logo mais il y a des règles spéciales que le jury doit suivre:

-Un jury peut voter pour 3 logos maximum, le premier logo pour qui il vote gagne 3 points, le deuxième 2 points et le troisième 1 point.

-Le logo gagnant est celui qui a eu plus de points.

-En cas d'égalité le gagnant est celui qui a reçu le plus de votes à la première place.

-En cas d'égalité encore le gagnant est celui qui a eu le plus de votes à la deuxième place.

-En cas d'égalité, tous sont déclarés gagnants.

## SOLUTION C++:
```cpp
#include <bits/stdc++.h>

using namespace std;
using str=string;

const  int MOD=1000*1000*1000+7;
const str alphabet="abcdefghijklmnopqrstuvwxyz";

#define pii pair<ll int,ll int>
#define psi pair<str, ll int>
#define pis pair<ll int, str>
#define msi map<str, ll int>
#define mis map<ll int, str>
#define vec vector
#define ll long long
#define ull unsigned long long


#define for_n(i,n) for(ll int i=0; i<n; ++i)
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

    for(ll int i=0;i>=0;i++)
    {

        ll int N;
        cin>>N;
        if(N==0) return;
        map<ll int,ll int [3]> result{};
        set<ll int> mval{};
        vec<ll int> score{3,2,1};
        for_n(k,N){
            
        
            ll int di;
            cin>>di;
            for_n(j,di)
            {
                
                ll int x;
                cin>>x;
                if(findIn(mval,x)==mval.en){
                    mval.ins(x);
                    (result[x])[0]=0;
                    (result[x])[1]=0;
                    (result[x])[2]=0;
                }
                (result[x])[j]+=score[j];
            }
             }
                
            vector<pii> classement{};

        for(auto& val: result)
        {
            classement.pb(make_pair((val.second[0]+val.second[1]+val.second[2]),val.first));
        }

        sort(all(classement), greater<pii>());

        for(auto it=classement.be;it!=classement.en;it++)
        {
            if((*it).first<classement.front().first)
                *it=classement.front();
        }

        while(find(classement.begin()+1,classement.en,classement.front())!=classement.en)
            classement.erase(find(classement.begin()+1,classement.en,classement.front()));

        if(classement[0].first>classement[1].first)
        {
           cout<<classement[0].second<<endl;
            
            continue;
        }

        /*for(auto val: classement)
           cout<<val.second<<" "<<val.first<<endl;*/

        vector<pii> premier{};
        vector<pii> deuxio{};

        for(auto val: classement)
        {
            premier.pb(make_pair(result[val.second][0],val.second));
        }

        sort(all(premier), greater<pii>());
        for(auto it=premier.be;it!=premier.en;it++)
        {
            if((*it).first<premier.front().first)
                *it=premier.front();
        }

        while(find(premier.begin()+1,premier.en,premier.front())!=premier.en)
            premier.erase(find(premier.begin()+1,premier.en,premier.front()));
        
        if(premier[0].first>premier[1].first)
        {
           cout<<premier[0].second<<endl;
            continue;
        }

        for(auto val: premier)
        {
            deuxio.pb(make_pair(result[val.second][1],val.second));
        }
        sort(all(deuxio), greater<pii>());
        for(auto it=deuxio.be;it!=deuxio.en;it++)
        {
            if((*it).first<deuxio.front().first)
                *it=deuxio.front();
        }

        while(find(deuxio.begin()+1,deuxio.en,deuxio.front())!=deuxio.en)
            deuxio.erase(find(deuxio.begin()+1,deuxio.en,deuxio.front()));
        
        if(deuxio[0].first>deuxio[1].first)
        {
           cout<<deuxio[0].second<<endl;
            continue;
        }

        vec<pii> resf{};

        for(auto& val: deuxio)
        {
            resf.pb(make_pair(val.second,val.first));
        }

        sort(all(resf));

        for(ll int w=0; w<resf.size()-1;w++)
        {
           cout<<resf[w].first<<" ";
        }
       cout<<resf.back().first<<endl; 
       
    }
}
           
 
int main()
{
    solve();
}
```


Au jour 4, j'ai résolu 3 exercices sur 5, j'ai donc occupé la sixième place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












