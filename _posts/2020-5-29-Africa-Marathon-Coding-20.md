---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 1
---
Mes Solutions au Jour 1 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 1

Il faut rappeler que chaque jour, une série de 5 exercices était donnés et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

## Problem A : Linear Equation 

### Sujet
You have been asked to write a program that can solve a simple linear equation. 

### Standard Input 
The first line of input contains a single integer P, (1 ≤ P ≤ 1000), which is the number of data sets that follow. Each data set consists of a single line containing one simple linear equation. All equations are strings of less than 200 characters. Each equation will be in the form of ax, followed by a single space, followed by a sign “+”, followed by b, followed by a single space ,followed by a sign “=”, followed by a single space, followed by c. *ax + b = c*

### Standard Output 
For each data set, generate two lines of output. The first line will contain “Equation n” where n is the number of the data set. The second line will contain the following answer: 
 
-If the equation has no solution, print "No solution.".
-If the equation has infinitely many solutions, print "More than one solution.".
-If the equation has exactly one solution, print "x = solution" where solution is replaced by the appropriate real number (printed to six decimals).
 
Print a blank line after each data set case.

#### Sample Input

5 

2x + 3 = 4 x = 0.500000

124x + 20 = 160

123456x + 7 = 2000

0x + 2 = 3

0x + 2 = 2 

#### Sample Output

Equation 1

x = 0.500000


Equation 2

x = 1.129032 


Equation 3

x = 0.016143 


Equation 4

No solution.


Equation 5

More than one solution.




### Réflexion
Facile! Vous me direz! Eh ben non, personne , n'a résolu cet exercice. Il y avit un petit piège. En faite quand on affiche simplement le résultat de (c-b)/a, pour certains cas on a une erreur de précision. Il fallait donc contourner ce problème en récupérant la partie entière et la partie décimale à l'aide d'un modulo.
Nous avons donc les formules suivantes:

*-partieEntiere= (c-b) / a*

*-partieDecimale= (c-b) % a *1000000 /a*

Voici ma solution:
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




        int main(){
            
            int T;
            cin>>T;

            for_n(i,T)
            {
                ll int a, b, c;
                scanf("%lldx + %lld = %lld",&a,&b,&c);

                printf("Equation %d\n",i+1);
                if(a!=0)
                {
                    ll int partiEntiere=(c-b)/a;
                    ll int partieDecimale=abs(c-b)%a*1000000/a;
                    if(partiEntiere==0 && c-b<0)
                        printf("x = -%lld.%6lld\n\n",partiEntiere,partieDecimale );
                    else
                    {
                        printf("x = %lld.%6lld\n\n",partiEntiere,partieDecimale );
                    }
                    

                }
                else
                {
                    if(c-b!=0)
                        printf("No solution.\n\n");
                    else
                    {
                        printf("More than one solution.\n\n");
                    }
                    
                    
                }
                
            }
        }

```

Pas si évident en fin de compte. Ah cet exercice, on s'en souviendra longtemps.

## Problem B: Vote 

### Sujet

Benin is organizing a presidential election the 06th march 2016. Several candidates submitted their applications for this presidential election. The CENA called “Commission Nationale Electorale Autonome” is responsible for managing the election. 
 
According to Article 15 of the beninese electoral code, the CENA is responsible for the preparation, the organization, the supervision of voting and for the centralization of the results. 
 
As a great programmer, you are asked to help the CENA to centralize the results of the presidential election. 

### Standard Input 
The first line of input contains a single integer P, (1 ≤ P ≤ 1000), which is the number of data sets that follow. Each data set consists of a line containing the number n of the candidates (1 ≤ n ≤ 100), a space and the number m of results to centralize (1 ≤ m ≤ 1000) and followed by n lines and m lines. The n lines contain the names of candidates, one per line. The m lines contain each a name X of one candidate, a space, the result R of the candidate and the center C of vote. X and C are strings that will contain at most 1000 characters. R is a positive integer.

### Standard Output 
For each data set, if there is only one winner, generate one line of output with the text *“VOTE i: THE WINNER IS ” followed by the name of the winner*, followed by space and followed by the total result of the winner. If not, generate the following output: *“VOTE i: THERE IS A DILEMMA”*. i is the number of the data set.

### Sample Input

2
 
3 4
 
Bignon
 
Akwaba
 
Sessi
 
Bignon 1000 Gbegamey
 
Sessi 1000 Yenawa
 
Akwaba 5 Vodje
 
Akwaba 996 Yenawa
 
2 3
 
Sena
 
Sedjro
 
Sedjro 6003 Malanville
 
Sena 6000 Kpankpan
 
Sena 3 Godomey

#### Sample Output
VOTE 1: THE WINNER IS Akwaba 1001

VOTE 2: THERE IS A DILEMMA
  

### Réflexion
Ici, pas de difficulté, il fallait utiliser un tableau associatif(map en c++) dans lequel on stock les votes de chaque candidat puis à la fin il faut trier le tableau par ordre décroissant. Si les deux premiers éléments du tableau ont le même nombre de votes, on affiche qu'il y a un dilemme, sinon le nom du premier éléments dans le tableau.

Voici ma solution:
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
            

            int N;
            cin>>N;

            for_n(i,N)
            {
                msi vote{};
                vec<pis> res{};
                int u, v;
                cin>>u >>v;

                for_n(j,u)
                {
                    str name;
                    cin>> name;
                    vote[name]=0;
                }
                for_n(j,v)
                {
                    str name, city;
                    int x;
                    cin>> name>>x>>city;
                    vote[name]+=x;
                }

                for(auto& val: vote)
                {
                    res.pb(make_pair(-val.second,val.first));
                }

                sort(all(res));

                if(res[0].first==res[1].first)
                    cout<<"VOTE "<<i+1<<": "<<"THERE IS A DILEMMA"<<endl;
                else
                    cout<<"VOTE "<<i+1<<": "<<"THE WINNER IS "<<res[0].second<<" "<<-res[0].first<<endl;

                
            }
        }

        int main()
        {
            solve();
        }
```

## Problem C : Square 

### Sujet
Do you know a game called “La cave aux énigmes”? One of its questions is to find the number of squares contained in a grid square of length l. A grid square of length 4 will look like this:


![_config.yml]({{ site.baseurl }}/images/AMCC/square.png)

The total number of squares that can be seen in this image is 30. Your task is to find the total number of squares which can be seen in an image of a grid square of length l. 

### Standard Input 

The input will begin with a single integer P on the first line, indicating the number of cases that will follow. 
 
The remaining lines of the input will consist of one integer l per line, which is the grid square length. All integers will be less than 1,000,000 and greater than 0. 
 
You should process all integers and for each integer l, determine the total number of squares which can be seen in an image of a grid square of length l. 
 
You can assume that no operation overflows a 32-bit integer.

### Standard Output

For each integer l, you should output the total number of squares which can be seen in an image of a grid square of length l, with one line of output for each line of input. 

#### Sample Input
4

1

2

3

4

#### Sample Output
1

5

14

30

### Réflexion

Certains ont peut-être trouvé une formule ici mais moi j'ai vu un pattern que je me suis contenté d'implémenter. En réalité, on remarque que le résultat pour une taille n, est le résultat de n-1 auquel on ajoute n*n.

Voici ma solution:
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


    ull int square(ull int x)
    {
        if(x==1) return 1;
        return square(x-1)+x*x;
    }


    void solve()
    {
        int N;
        cin>>N;

        for_n(i,N)
        {
            ull int x;
            cin>>x;
            cout<<square(x)<<endl;
        }
    }

    int main()
    {
        solve();
    }
```

## Problem E : X X glued 

### Sujet

Do you know the game "X X glued" practiced on the registration plates of Benin cars by children? 
 
A beninese car registration number is written in the form of VY ABCD RB or Y ABCD RB. For example, AC 2554 RB and X 6006 RB are beninese car registration numbers. The game "X X glued" is to quickly verify that there is in the number two identical consecutive digits or not. The winner is the first child that pronounces "X X collés" and shows the car with his finger. 
 
 
 
### Standard Input 
The input contains several lines and ended with the # character on a single line. Other lines each contain a single registration number as VY ABCD RB or Y ABCD RB. 
 
 
 
### Standard Output 
For each registration number, your program should display on one line, all the "X X glued" in the format shown in the example. If there is no "X X glued" in the number, the program should display nothing.

#### Sample Input 
X 6006 RB

AC 2233 RB

T 2000 RB

F 2345 RB

AB 4444 RB

#

#### Sample Output

0 0 glued

2 2 glued and 3 3 glued

0 0 glued

4 4 glued

### Réflexion

Ici, je pense que la difficulté était d'extraire la série de 4 lettres. Puisque l'entrée était sur le format *A B C*, j'ai déclaré trois string A, B, C et je n'avais plus que B à traîter.

Voici ma solution:

```cpp

    #include <bits/stdc++.h>
    #include <iomanip>

    using namespace std;
    using str=string;
    using ll=long long;
    using ull= unsigned long long;
    const int MOD=1000*1000*1000+7;
    const str alphabet="abcdefghijklmnopqrstuvwxyz";

    #define pii pair<int,int>
    #define psi pair<str, int>
    #define pis pair<int, str>
    #define msi map<str, int>
    #define mis map<int, str>
    #define vec vector


    #define for_n(i,n) for(int i=0; i<n; ++i)
    #define pb(x) push_back(x)
    #define ins(x) insert(x)
    #define all(x) x.begin(),x.end()
    #define findIn(x,y) find(all(x),y)

    void solve()
    {
        str A, B, C;

        

        for_n(i,MOD)
        {
            cin>>A;
            if(A=="#") return ;
            set<char> G{};

            cin>>B>>C;
            
            for(int i=1; i<B.size(); ++i)
            {
                if(B[i-1]==B[i])
                    G.ins(B[i]);
            }

            if(G.size()==1)
                cout<<*(G.begin())<<" "<<*(G.begin())<<" glued"<<endl;
            else if(G.size()==2){
                cout<<*(G.begin())<<" "<<*(G.begin())<<" glued and ";
                G.erase(G.begin());
                cout<<*(G.begin())<<" "<<*(G.begin())<<" glued"<<endl;
            }

            
        }
        
    }

    int main()
    {
        solve();
    }
```

A la fin j'ai donc résolu 3/5 exercices, ce qui m'a permis de prendre la 7ème place du classement ce jour!

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












<!--[_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.-->
