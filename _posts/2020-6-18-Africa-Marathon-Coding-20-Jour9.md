---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 9
---
Mes Solutions au Jour 9 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 9

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem A: Burkina Faso 

### Sujet

There are at least three telecom operators in Burkina Faso [Airtel, Onatel (Office National des Telecommunications) and Telecel Faso]. Each operator has different prices for call and data usage, given in the table below. All prices are in XOF (FCFA) : 
 
![reseau]({{ site.baseurl }}/images/AMCC/reseau.png)
 
Some foreign students have arrived Burkina Faso to participate in the Marathon Challenge, Ouagadougou Site. They already know how many minutes they will call, and how much Internet they will use. For each student, you want to recommend an operator to minimize the total cost of call usage and data usage for that student.  

### Standard Input 

 Each line of the input contains the information of one student. For each student, there are two positive integers c and d (1 ⩽ c, d ⩽ 1000) that show the amount of call (in minutes) and data usage (in megabytes) for the student, respectively. The input terminates with “0 0” that should not be processed.

### Standard Output 

For each student, print a line containing the minimum total cost of call usage and data usage.  

![day9A]({{ site.baseurl }}/images/AMCC/day9ioA.png)

### Réflexion

Les étudiants à Ouagadougou veulent savoir quel réseau leur sera économique en fonction du nombre de minutes **c** d'appels qu'ils auront à faire et du nombre de mégabytes **d** qu'ils auront à utiliser.

Donc pour chaque réseau on va calculer le cout en faisant 

***c * CoûtParMinute + d * CoûtParMb*** 

A la fin on affiche le coût minimum.


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
    int c,d;
    while(cin>>c>>d, c||d)  cout<<min(min(c*30+d*40,c*40+d*20),c*35+d*30)<<endl;
    
}

int main()
{
    solve();
}

```

## Problem B: Payment card 

### Sujet

An android market, is looking for creative software developers. A group of applicants are attending an interview, and the company wants to select the fastest developer who can code simple rules accurately. As a test, all applicants should quickly develop a bank card verifier that determines whether a payment card number is valid or not. 
 
All payment card numbers are 16 digits long. The leftmost 6 digits represent a unique identification number for the bank who has issued the card. The next 2 digits determine the type of the card (e.g., debit, credit, gift). Digits 9 to 15 are the serial number of the card, and the last digit is used as a control digit to verify whether the card number is valid. Hence, if somebody enters the card number incorrectly, there is a high chance that a payment software can easily determine it. 
 
For a valid card number, the last digit is selected in such a way that the following algorithm passes: 
 
1. Label all digits from left to right by 1 to 16.
2. Multiply each odd-labeled digit by 2.
3. If the result for any digit is greater than 9, subtract 9 from it.
4. Sum the results of the previous step, and add to it the sum of all even-labeled digits.
5. If the result is a multiple of 10, the card number is valid; otherwise, it is invalid. 
 
Your task is to read several card numbers from the input, and determine whether each one is a valid card number or not.

### Standard Input

There are multiple test cases in the input. Each test is given in one line consisting of four spaceseparated 4-digit strings. The leftmost digit of the given card number is guaranteed to be nonzero. The input terminates with a line containing “0000 0000 0000 0000” that should not be processed.  

### Standard Output

For each test case, output a line containing “Yes” or “No” depending on whether the card number is valid or not, respectively. 
 
![ExampleDay9]({{ site.baseurl }}/images/AMCC/day9ioB.png)

### Réflexion

Ici on veut vérifier la validité des cartes bancaires. On fera donc une fonction qui vérifie les conditions ci-dessus et afficher **YES** si la carte est valide et **NO** si elle ne l'est pas.

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


int ord(char x)
{
    return (int)x-48;
}


bool validCard(str& card)
{
    if(card.size()!=19) return false;

    while(findIn(card,' ')!=card.en)
        card.erase(findIn(card,' '));

    vec<int> mullabel{};

    for(int i=1;i<=card.size();i+=2)
    {
        
        
            mullabel.pb(ord(card[i-1])*2);
       
    }

    int res=0;

    for(auto& val: mullabel)
    {
        if(val>9) val-=9;

        res+=val;
    }

    for(auto i=0; i<card.size(); i+=2)
    {
        res+=ord(card[i+1]);
    }

    if(res%10!=0) return 0;

    return 1;



}



void solve()
{
    

    while(1)
    {
       str card;
       getline(cin,card);
       cin.clear();

       if(card=="0000 0000 0000 0000") return;

       (validCard(card))? cout<<"Yes"<<endl:  cout<<"No"<<endl;

      
    }
    
}

int main()
{
    solve();
}

```


Au jour 9, j'ai résolu 2 exercices sur 5, j'ai occupé la 12 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












