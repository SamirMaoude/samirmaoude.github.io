---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 3
---
Mes Solutions au Jour 3 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 3

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem A : Progression 

### Sujet
According to Wikipedia, an arithmetic progression (AP) is a sequence of numbers such that the diﬀerence of any two successive members of the sequence is a constant. For instance, the sequence 3, 5, 7, 9, 11, 13, . . . is an arithmetic progression with common diﬀerence 2. For this problem, we will limit ourselves to arithmetic progression whose common diﬀerence is a nonzero integer.

On the other hand, a geometric progression (GP) is a sequence of numbers where each term after the ﬁrst is found by multiplying the previous one by a ﬁxed non-zero number called the common ratio. For example, the sequence 2, 6, 18, 54, . . . is a geometric progression with common ratio 3. For this problem, we will limit ourselves to geometric progression whose common ratio is a non-zero integer.

Given three successive members of a sequence, you need to determine the type of the progression and the next successive member.  

### Standard Input 
Your program will be tested on one or more test cases. Each case is speciﬁed on a single line with three integers (−10, 000 < a1, a2, a3 < 10, 000) where a1, a2, and a3 are distinct.

The last case is followed by a line with three zeros. 

### Standard Output 
For each test case, you program must print a single line of the form: 
 
XX v 
 
where XX is either AP or GP depending if the given progression is an Arithmetic or Geometric Progression. v is the next member of the given sequence. All input cases are guaranteed to be either an arithmetic or geometric progressions. 

#### Sample Input

4 7 10

2 6 18

0 0 0 

#### Sample Output

AP 13

GP 54


### Réflexion

Ah ça commence bien, petit exo pour se mettre en jambes.

On nous donne une série de trois nombre représentant une suite arithmétique ou une suite géométrique. Et il faut qu'on affiche le terme suivant de la suite.

Pour le faire on va vérifier si la suite est arithmétique en vérifiant si a2-a1 = a3-a2.

Si  C'est le cas on affiche **AP a3+(a3-a2)**

Si ce n'est pas le cas, d'après le sujet il s'agit forcément d'une suite géométrique et on affiche **GP a3\*(a3/a2)**
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
#define findIn(x,y) find(all(x),y)


void solve()
{
    for(int i=0;i>=0;i++)
    {
        ll int a1,a2,a3;
        cin>>a1>>a2>>a3;
        if(a1==0 && a2==0 && a3==0)
            return;
    (a2-a1==a3-a2)? cout<<"AP "<<2*a3-a2<<endl: cout<<"GP "<<a3*a3/a2<<endl;
        


    }
}

int main()
{
    solve();
}

```


## Problem B: Kids 

### Sujet

Your son's birthday is corning soon (assume that you have a son), and you promised to make the best party ever for him. He will be very happy if he can invite all his friends to this party (he has many friends), but unfortunately you can't invite everyone because you have a limited number of candies, and you want everyone to be happy. 
As we all know, kids love to eat a lot of candies of the same type, let's say a kid will be happy only if he can eat at least K candies of the same type. 
Given K, and the number of available candies of each type, calculate the maximum number of kids where you can make all of them happy by giving each one at least K candies of the same type.

### Standard Input

Your program will be tested on one or more test cases. The first line of the input will be a single integer T, the number of test cases (1 ≤ T ≤ 100). Followed by the test cases, each test case is on two lines. The first line of each test case contains two integers N, the number of different candies (1 ≤ N ≤ 100), and K, the minimum number of candies which will make a kid happy as described above (1 ≤ K ≤ 100). The second line of each test case contains N integers, separated by a single space, which are the available number of candies of each type. There will be at least 1 candy and at most 100 candies of each type. 


### Standard Output

For each test case, print on a single line one integer, the maximum number of kids you are asked to calculate as described above.


### Sample Input

2

3 2

4 5 7

3 8

4 5 7 
#### Sample Output

7

0

### Réflexion

Pour la fête, un enfant est heureux s'il mange K bonbons du même type. Sachant que vous avez N types de bonbons de quantités différentes, vous devez déterminer le nombre maximum d'enfants à inviter pour que tous soient heureux.

Pour un bonbon de quantité q, le nombre de fois qu'il contient K bonbons est le nombre d'enfants qu'il peut rendre heureux soit la division entière de q par K.

Donc il faut faire ce calcul pour les N types de bonbons et afficher la somme de tous ces N résultats.

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
#define findIn(x,y) find(all(x),y)


void solve()
{
    int N;
    cin>>N;
    for_n(i,N)
    {
        int res=0,n,k;

        cin>>n>>k;

        for_n(j,n)
        {
            int x;
            cin>>x;
            res+=x/k;
        }

        cout<<res<<endl;

    }
}

int main()
{
    solve();
}

```


## Problem C : Fuel 

### Sujet

The government of Africaland has recently announced a new petrol rationing plan with an unexpected price hike. According to the new plan, each person receives a quota of 60 liters per month in a fuel card. Each liter of petrol costs 1500 nairas if it is within quota. Any extra fueling costs 3000 nairas per liter. 
 
After recovering from the shock, Mahya is trying to figure out how dark is the future. The current month is coming to an end, and Mahya has some quota left in her fuel card, remaining available for the next month. A quota of 60 liters will also be added to her fuel card just at the beginning of the next month. She also has a prediction of the amount of petrol that will be used in the next month. She now wants to know how much she should pay for petrol in the next month. However, she is too lazy to do that on her own. So, she needs your help to calculate the cost for her.

### Standard Input 

The first line of input contains an integer N which is the number of datasets that follow.   Each dataset consists of two lines. The first line contains an integer n (0 ⩽ n ⩽ 200), specifying the amount of petrol that will be used in the next month. The second line contains an integer k (0 ⩽ k ⩽ 360), showing the quota left in Mahya’s fuel card at the end of current month.

### Standard Output

For each dataset, print out on a single line, the amount of money (in nairas) that Mahya will pay for petrol in the next month.

#### Sample Input
2

41

0

125

40 

#### Sample Output

61500

225000

### Réflexion

Mahya veut prévoir le montant quel va dépenser pour sa consommation au cours d'un mois. Mais la société où elle prend son carburant a ses propres règles:

Elle fait une réduction sur les 60 premiers litres et les vend à 1500 le litre

Si le client avait un quota Q qu'il n'avait pas utilisé le précédent mois, cette quantité lui sera facturée aussi à 1500 le litre

Pour tout autre excédent, le litre est facturé à 3000

Donc Mahya va fournir la quantité E de carburant qu'elle compte utiliser au cours du mois et le quota Q qu'il lui restait le mois précédent. De là pour calculer les dépenses de Mahya on a deux formules:

Si (E<= Q+60) alors depense = E*1500

Sinon depense = (Q+60)*1500+(E-Q-60)-3000

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
#define findIn(x,y) find(all(x),y)

void solve()
{
    int N;
    cin>>N;
    for_n(i,N)
    {
        int E,Q;
        cin>>E>>Q;
        if(E<=Q+60)
            cout<<E*1500<<endl;
        else
        cout<<(60+Q)*1500+(E-60-Q)*3000<<endl;
    }
}

int main()
{
    solve();
}

```


##  Problem E : Emails   

### Sujet

This year, many people registered for the internet contest with several email addresses. We want to see how many valid and distinct email addresses registered. 
 
A valid email address consists of a username and a domain name separated by a character ‘@’. A username is a string containing letters (a-z and A-Z), digits (0-9), underscores (_), and periods (.). Usernames cannot begin or end with a period and cannot contain two consecutive periods. Other than this rule, periods do not matter in email addresses (they can be removed without changing the address). Uppercase and lowercase letters in the usernames are considered the same. So, usernames AliBaba and ali.baba are considered the same. Usernames should contain 6 to 30 characters, after removing all of its periods. 
A valid domain name is a string of length between 3 and 30 (inclusive), consisting of domain parts separated by periods (.). A domain name must not start or end with a period. Each domain part is a non-empty string of letters (a-z and A-Z), digits (0-9), and dash (-). Uppercase and lowercase letters in the domain names are also considered the same. So, Foo.bar is the same as foo.Bar, but not the same as Foo-Bar or Foobar.

### Standard Input 

The first line of input contains a single integer P, (1 ≤ P ≤ 1000), which is the number of data sets that follow. The first line of the dataset contains a positive integer n (1 ⩽ n ⩽ 1000), the number of the registered email addresses. Each of the next n lines contains one email address of length at most 100 and consisting of alphabets, digits, ‘@’, ‘.’, ‘_’, and ‘-’.

### Standard Output

For each input data set, the output is a line containing a single integer which is the number of distinct email addresses that are valid. 

#### Sample Input
1

5

acmacm@icpc.ir

acmacm..a@icpc.ir

.a1a1.abc@icpc.ir

acma.c.m@icpc.ir

acmacm@icpc.com 

#### Sample Output

2

### Réflexion

Ici il s'agit de trouver le nombre de mails valides différents

Donc il faut une fonction qui vérifie la validité d'un mail suivant les conditions du sujet.

Si un mail est valide, il faut supprimer tous les points contenus dans le nom d'utilisateur et l'introduire dans un conteneur de type [set](http://www.cplusplus.com/reference/set/set/).

Un conteneur de type set ne stocke que des éléments uniques. Donc quand on va vouloir introduire un mail qui est déjà contenu dans le set, il ne va pas l'introduire à nouveau.

Alors puisqu'on est sûr que tous les mails dans le set sont uniques et valides, il ne nous reste plus qu'à afficher le nombre d'éléments que contient le set comme résultat.


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
#define findIn(x,y) find(all(x),y)


pair<bool,str> validMail(str& mail)
{
    str valuser=alphabet+"0123456789_.";
    str valdomain=alphabet+"0123456789-.";
    if(findIn(mail,'@')==mail.en)
        return make_pair(0,mail);

    
    str user="";
    //str domainc="";
    str domain="";

    for(auto it=mail.be;it!=findIn(mail,'@');it++)
        user+=(char)tolower(*it);
    for(auto it=findIn(mail,'@')+1;it!=mail.en;it++)
        domain+=(char)tolower(*it);

    if(user.front()=='.' || user.back()=='.' || domain.front()=='.')
        return make_pair(0,mail);

    if(findIn(domain,'.')==domain.en)
        return make_pair(0,mail);

    for(auto x: user)
    {
        if(findIn(valuser,x)==valuser.en)
            return make_pair(0,mail);
    }

    for(int k=1;k<user.size();k++)
    {
        if(user[k]=='.' && user[k-1]=='.')
        {
            return make_pair(0,mail);
        }
    }

    int sizeuser=0;

    for(auto it=user.be;it!=user.en; it++)
    {
        if(*it!='.')
            sizeuser++;
    }

    


    if((sizeuser<6 || sizeuser>30)) return make_pair(0,mail);

    if(domain.front()=='.' || domain.back()=='.')
       make_pair(0,mail);
    if((domain.size()<3 || domain.size()>30)) return make_pair(0,mail);

    for(auto x: domain)
    {
        if(findIn(valdomain,x)==valdomain.en)
           return make_pair(0,mail);
    }

    if(findIn(domain,'.')==domain.en)
        return make_pair(0,mail);

    while(findIn(user,'.')!=user.en)
        user.erase(findIn(user,'.'));

    user+="@"+domain;
    return make_pair(1,user);

    
}


void solve()
{
    int N;
    cin>>N;

    for_n(i,N)
    {
        int n;
        cin>>n;
        set<str> mails{};
        for_n(j,n)
        {
            
            str mail;
            cin>>mail;
            if(validMail(mail).first)
            {
                mails.ins(validMail(mail).second);
            }
            
        }


        cout<<mails.size()<<endl;
    }
    
}

int main()
{
    solve();
}

```

Au jour 3, j'ai résolu 4 exercices sur 5, j'ai donc occupé la deuxième place du classement (petite vengeance par rapport à la veille, ça fait plaisir haha).

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












