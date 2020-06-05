---
layout: post
title: Africa Marathon Coding Challenge 2020 Jour 6
---
Mes Solutions au Jour 6 de l'Africa Marathon Coding Challenge 2020.

Du 29 Avril au 12 Mai dernier, la société MAPCOM avait organisé une compétition d'algorithmique en vue d'occuper les étudiants africains et par ricochet leur permettre d'améliorer leur compétences en programmation, en ces temps de COVID-19. J'ai participé à cette compétition qui réunissait les étudiants de lAngola, du Bénin,du Burkina-Faso, du Nigéria, du Sénégal et du Togo. Je vais vous présenter mes solutions des problèmes que j'ai résolu.

# Jour 6

Il faut rappeler que chaque jour, une série de 5 exercices qu'il fallait résoudre en 5h était donnée et à la fin il y avait un classement en fonction de celui qui a résolu le plus d'exercices en moins de temps.

##  Problem A: Sum 

### Sujet

For this problem you will compute various running sums of values for positive integers 

### Standard Input 

The first line of input contains a single integer P, (1 <=  P <= 10000), which is the number of data sets that follow. Each data set should be processed identically and independently. 
 
Each data set consists of a single line of input. It contains the data set number, K, followed by an integer N, (1 <= N <= 10000). 

### Standard Output 

For each data set there is one line of output. The single output line consists of the data set number, K, followed by a single space followed by three space separated integers S1, S2 and S3 such that: 
 
**S1 = The sum of the first N positive integers.**
    
**S2 = The sum of the first N odd integers.**
    
**S3 = The sum of the first N even integers.**

#### Sample Input

3

1 1

2 10

3 1001 

#### Sample Output

1 1 1 2

2 55 100 110

3 501501 1002001 1003002 

### Réflexion

Pour un certain N, on demande:

-la somme des N premiers entiers positifs, ce qui est donnée par la formule suivante: **N(N+1)/2**

-la somme des N premiers entiers impaires, ce qui est égale à **N²**

-la somme des N premiers entiers paires, ce qui est égale à **N(N+1)**



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
    int T;
    cin>>T;
    while(T--)
    {
        int K,N;
        cin>>K>>N;

        cout<<K<<" "<<N*(N+1)/2<<" "<<N*N<<" "<<N*(N+1)<<endl;


    }
}

int main()
{
    solve();
}

```


##  Problem B: Programming language 

### Sujet

Programming languages such as C++ and Java can prefix characters to denote the base of constant integer values. For example, hexadecimal (base 16) constants are preceded by the string **“0x”**. Octal (base 8) values are preceded by the character **“0”** (zero). Decimal (base 10) values do not have a prefix. For example, all the following represent the same integer constant, albeit in different bases.

0x1234

011064

4660

The prefix makes it clear to the compiler what base the value is in. Without the “0x” prefix, for example, it would be impossible for the compiler to determine if 1234 was hexadecimal. It could be octal or decimal. 
 
For this problem, you will write a program that interprets a string of decimal digits as if it were an octal value, a decimal value or a hexadecimal value.

### Standard Input

The first line of input contains a single decimal integer P, (1 <= P <= 10000), which is the number of data sets that follow. Each data set should be processed identically and independently. 
 
Each data set consists of a single line of input. It contains the data set number, K, followed by a single space, followed by a string of at most 7 decimal digits.  

### Standard Output

For each data set there is one line of output. The single output line consists of the data set number, K, followed by a space followed by 3 space separated decimal integers which are the value of the input as if it were interpreted to as octal, decimal and hexadecimal respectively. If the input value cannot be interpreted as an octal value, use the value 0. 
 
### Sample Input

4

1 1234

2 9

3 1777

4 129 

#### Sample Output

1 668 1234 4660

2 0 9 9

3 1023 1777 6007

4 0 129 297 

### Réflexion

On vous donne un nombre décimal X en entrée , si X peut être interprèté comme un nombre octal alors vous devez afficher

**X en base 10, X et X en base 16**

Sinon vous affichez **0 X et X en base 16**

### SOLUTION PYTHON 3:

```py


for _ in(range(int(input()))):
    K,x= input().split(' ')
    try:
        print(K,int("0o"+x,8),x,int("0x"+x,16))
    except:
        print(K,0,x,int("0x"+x,16))

```

##  Problem D: NASA 

### Sujet

After NASA discovered water on Mars, they decided to expand their exploration hoping to find some alien intelligence on the planet. After months of exploration, they were actually surprised to find out that the planet has been inhabited by minions. 

NASA started communications with the minions and the first message they received was Mo amo Banana. At first, it was really hard to decipher the message but after sometime they managed to workout a dictionary that maps English words to Minionese words. You are going to help NASA build the translator to ease their communication with Minions for the good and prosperity of mankind and minionkind.

### Standard Input

The first line of input will contain a single integer N, the number of words in the dictionary (1 ≤ N ≤ 100). The following N lines will each contain a sentence of the format x = y where x is an English word and y is a Minionese word. The next line will contain an integer T, the number of test cases (1 ≤ T ≤ 100). Each test case will start with a line containing an integer K, the number of words in the sentence (1 ≤ K ≤ 100) and the next line will contain K space separated English words. All the English words in the test cases exist in the defined dictionary. Also, all the words consist only of English alphabet, and will be at most 20 characters long.

### Standard Output

For each test case, print a single line containing the space separated Minionese words after translation.
 
### Sample Input

4

I = mo

love = amo

icecream = gelatooo

banana = banana

2

3

I love banana

3

I love icecream 

#### Sample Output

mo amo banana

mo amo gelatooo

### Réflexion

On doit construire un traducteur entre les minions et les humains. Tout d'abord on nous donne des mots en anglais puis leurs équivalents dans le langage des minions et à la fin nous devons traduire des phrases minions en anglais.

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
    map<str,str> dico{};
    int T;
    cin>>T;

    while(T--)
    {
        str english, extra, o;
        cin>>english>>o>>extra;
        dico[english]=extra;
    }

    cin>>T;

    while(T--)
    {
        int n;
        cin>>n;
        str res="";
        for_n(j,n)
        {
            str word;
            cin>>word;
            res+=dico[word]+" ";

        }
        res.pop_back(); 
        cout<<res<<endl;
    }
    
}

int main()
{
    solve();
}

```

##  Problem E: Quiz

### Sujet

The minions have finally found their new master. This time, he is a Math professor and he is trying very hard to teach them math. He has been teaching them bitwise operators for over a year! They learnt about AND **(&)** and OR **(\|)** operators and it is time for a quiz to test them. 

The quiz is very simple, they will be given a number A of AND **(&)** operators, a number B of OR **(\|)** operators and **(A + B + 1)** integers. They have to find the maximum number that can be obtained by inserting the & and \| operators between the given nonnegative integers without changing their order. 
Finally, there is a special requirement for this quiz, they are required to evaluate the operators from left to right.

### Standard Input 

The first line of the input will be a single integer T, the number of test cases **(1 ≤ T ≤ 100)**, followed by T test cases. 

Each test case will consist of 2 lines. The first line will contain 2 integers **A** and **B (0 ≤ A, B ≤ 10000)** representing the number of **AND (&)*** and **OR (\|)** operators, respectively. The second line of input will consist of **(A + B + 1)** 64-bit nonnegative integers separated by single spaces. 

### Standard Output 

For each test case, output a single line containing the maximum number that can be obtained by inserting the operators between the given integers. 

#### Sample Input

2

1 1

1 4 5

2 2

2 3 11 4 5 

#### Sample Output

5

7

### Réflexion

Un professeur veut enseigner le **"ET bit-à-bit (&)"** et le **"OU bit-à-bit"** aux minions.

###### &(ET bit-à-bit)	Retourne 1 si les deux bits de même poids sont à 1
9 & 12 (1001 & 1100) donne 8 (1000)
###### \|(OU bit-à-bit)	Retourne 1 si l'un ou l'autre des deux bits de même poids est à 1 (ou les deux)	
9 \| 12 (1001 \| 1100) donne 13 (1101)


On nous donne un nombre A de & et un nombre B de \| qu'on va insérer successivement entre A+B+2 entiers et sortir le résultat



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

void solve(){
    int T, a,b;

    cin>>T;
    while(T--){

        cin>> a>> b;

        int numbers[a+b+1];

        for_n(i,a+b+1) cin>>numbers[i];

        int res=numbers[0];

        for(int i=1; i<=a ;i++) res=res & numbers[i];

        for(int i=a+1;i<=a+b;i++) res=res \| numbers[i];

        cout<<res<<endl;
    }

}

int main()
{
    solve();
}

```


Au jour 6, j'ai résolu 4 exercices sur 5, j'ai occupé la 8 ème place du classement.

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.












