---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 7
---
Mes Solutions au Jour 7 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 7

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem A: Kings 

### Sujet

Mahya loves to know more about the history of her country. She is in particular interested in the history of the ancient kings of Persia. Recently, Mahya got curious to know how long each of her favorite kings had lived. So, she started searching the web, and collecting information about the kings lives. 
 
Unfortunately, in most cases, the exact dates on which the kings were born or died are not available in resources. So, Mahya could only find some ranges for possible dates of birth and death for each of the kings. For example, for Cyrus the Great, she could only find that the date of birth was between 600 BC and 575 BC, and the date of death was 530 BC. So, she concluded that Cyrus the Great had lived at least 45 years and at most 70 years. 

![king]({{ site.baseurl }}/images/AMCC/king.png)
 
Mahya has created a long list of her favorite kings, and for each king, has written down two ranges showing the birth range and the death range of that king. Since the list is a bit lengthy, she needs your help to process the list, and produce for each king the minimum and the maximum age. Note that if a king was born in year x and died in year y, then he lived y x years. 

### Standard Input 

There are multiple test cases in the input. Each test case consists of a line containing four integers a, b, c, d, where 5000 ⩽ a ⩽ b < c ⩽ d ⩽ 2000. The range [a, b] shows the birth range, and [c, d] shows the death range. The input terminates with 0 0 0 0 which should not be processed. 

### Standard Output 

For each test case, output a line containing the minimum and the maximum age as two integers separated by a space. 

#### Sample Input

100 110 180 185

-600 -575 -530 -530

-25 10 72 86

0 0 0 0 

#### Sample Output

70 85

45 70

62 111

### Réflexion

Mahya fait des recherches sur les anciens souverains de son pays et, elle aimerait connaitre combien de temps ces derniers ont vécu. Pour cela pour chaque souverain elle dispose un interval **\[a ,b]** contenant son année de naissance et un autre interval **\[c ,d]** contenant son année de décès. Nous devrons afficher pour chaque souverain le minimum **(c-b)** et le maximum **(d-a)** de temps qu'il a vécu.


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
    while(1)
    {
        int a,b,c,d;
        cin>>a>>b>>c>>d;
        if(!a && !b &&!c && !d) return;

        cout<<c-b<<" "<<d-a<<endl;
    }
}

int main()
{
    
    solve();
}

```


##  Problem B: HTML color 

### Sujet

![HTMLColor]({{ site.baseurl }}/images/AMCC/color.png)
### Standard Input

There are multiple test cases in the input. Each test case consists of a line containing three integers 0 ⩽ r, g, b ⩽ 255 which are the Red, Green and Blue intensities of the color, respectively. The input terminates with -1 -1 -1 which should not be processed. 

### Standard Output

For each test case, output a line containing the name of the closest HTML color to the given color. If there are more than one closest color, print the one which has a smaller associated number in the above table.
 
### Sample Input

120 120 10

111 112 113

5 135 8

-1 -1 -1 

#### Sample Output

Olive

Gray

Green 

### Réflexion

Nous avons un dictionnaire de couleurs HTML où chaque couleur a des valeurs RGB. On nous donne des valeurs r, g, b et nous devons déterminer la couleur la plus proche dans le dictionnaire en utilisant la formule ci-dessus.

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
#define mkt make_tuple


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
   map<string,tuple<int,int,int>> Color{};

   Color["White"]=make_tuple(255,255,255);
   Color["Silver"]=mkt(192,192,192);
   Color["Gray"]=mkt(128,128,128);
   Color["Black"]=mkt(0,0,0);
   Color["Red"]=mkt(255,0,0);
   Color["Maroon"]=mkt(128,0,0);
   Color["Yellow"]=mkt(255,255,0);
   Color["Olive"]=mkt(128,128,0);
   Color["Lime"]=mkt(0,255,0);
   Color["Green"]=mkt(0,128,0);
   Color["Aqua"]=mkt(0,255,255);
   Color["Teal"]=mkt(0,128,128);
   Color["Blue"]=mkt(0,0,255);
   Color["Navy"]=mkt(0,0,128);
   Color["Fuchsia"]=mkt(255,0,255);
   Color["Purple"]=mkt(128,0,128);

   while(1)
   {
       int r,g,b;
       cin >>r>>g>>b;
       if(r==-1 && g==-1 && b==-1) return;

       string res;
       double min=MOD;

       for(auto& val: Color)
       {
           double dx=pow(get<0>(val.second)-r,2) + pow(get<1>(val.second)-g,2) + pow(get<2>(val.second)-b,2);
           if(dx<min)
           {
               min=dx;
               res=val.first;
           }
       }
       cout<<res<<endl;
   }

    
}

int main()
{
    solve();
}

```


Au jour 7, j'ai résolu 2 exercices sur 5, j'ai occupé la 4 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












