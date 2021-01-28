---
layout: post
title: The Beninese Collegiate Programming Contest
---
Solutions des problèmes résolus par mon équipe.

Le 23 Janvier s'est déroulé le concours national de programmation au Bénin [**BCPC**](https://web.facebook.com/BeninCPC). Mon équipe a terminé deuxième à l'issu de ce concours avec 8 problèmes résolus.

Dans cet article, je vais tout d'abord présenter rapidement comment fonctionne ce concours, puis je vais passer sur chaque exercice que mon équipe a résolu, pour donner une explication de notre solution durant le concours.

# Le concours

Le principe du concours était le suivant:
* Plusieurs problèmes de difficultés diverses nous sont soumis
* Chaque problème est composé:

    * D'un énoncé donnant le contexte du problème, ainsi que le résultat attendu
    * D'une description des entrées et sorties (contraintes (ordre de grandeur des différentes valeurs), type des données)
    * D'un ou plusieurs exemples (entrée(s) et sortie(s) attendue(s))

A partir de ces informations fournies, l'objectif est de coder un programme dans un langage informatique parmi les langages proposés comme: *Python 3, C++, Java et le C*, qui va:
* Inclure le fichier dans lequel seront fournis les entrées (<span style="color:#e83e8c; background-color: #e4dcdc9e;">freopen("fichier.in","r",stdin);</span> en C/C++, <span style="color:#e83e8c; background-color: #e4dcdc9e;">sys.stdin = open("fichier.in","r")</span> en Python 3)
* Lire les entrées dans le fichier (<span style="color:#e83e8c; background-color: #e4dcdc9e;">cin</span> pour C++, <span style="color:#e83e8c; background-color: #e4dcdc9e;">scanf</span> pour C, <span style="color:#e83e8c; background-color: #e4dcdc9e;">input()</span> pour Python 3 par exemple)
* Renvoyer sur la sortie standard (<span style="color:#e83e8c; background-color: #e4dcdc9e;">cout</span> pour C++, <span style="color:#e83e8c; background-color: #e4dcdc9e;">printf</span> pour C, <span style="color:#e83e8c; background-color: #e4dcdc9e;">print()</span> pour python 3 ...) la réponse correspondante aux entrées


##   Problem A. Calculator Messages

### Sujet

Alex is a six-year-old boy. He was playing with his sister’s calculator and he discovered that when he
rotates the calculator, some digits look like characters. This is his list:
<div align="center">0 → O</div>
<div align="center">1 → I</div>
<div align="center">2 → Z</div>
<div align="center">3 → E</div>
<div align="center">5 → S</div>
<div align="center">7 → L</div>
<div align="center">8 → B</div>
<div align="center">9 → G</div>

Alex will write some digits for his mother on the calculator and she will need your help to translate them
into alphabetical words.



### Input 

The first line contains N - the number of Alex’s words (1 ≤ N ≤ 100).<br/>
Each of the N lines contain a string S<sub>i</sub> (1 ≤ |S<sub>i</sub>| ≤ 1000) and has only digits                     
[0, 1, 2, 3, 5, 7, 8, 9].
|X| is the length of X. 

### Output 

N lines; each has one string with uppercase English letters - the string you will give to Alex’s mother.

![Probleme_1_io]({{ site.baseurl }}/images/BCPC/a.png)

### Réflexion

Pour ce problème on nous donne un dictionnaire dans lequel on associe certains chiffres aux lettres de l'alphabet, l'objectif est de traduire un nombre donné et de l'inverser.

Durant le concours, nous avons utilisé la structure **dict**({}) de python. Cette structure permet de faire une association entre des clés et des valeurs. Les adeptes du C++ auraient pu utiliser la structure **map** de la bibliothèque standard qui est l'équivalente de **dict**.



### SOLUTION PYTHON 3:

```py

import sys

sys.stdin = open("digits.in", "r")

dico = {'0' : 'O','1' : 'I','2' : 'Z','3' : 'E','5' : 'S','7' : 'L','8' : 'B','9' : 'G'}

n = int(input())

for _ in range(n):

    res = ""

    for i in input(): res+=dico[i] #traduction

    print(res[::-1])

```

## Problem B. Winner

### Sujet

One day, a famous website made a 1 vs 1 contest. This is a special type of contest, in which 2 contestants
compete against each other in a contest that has N problems and the one who solves more problems first
wins.

*Mike* challenged his friend *Jack* on who will solve more problems first.

Can you help them and tell who solved more problems first, or if there’s a tie?

### Input

The input consists of 2 lines.

The first line contains an integer N (1 ≤ N ≤ 100) - the number of problems.

The second line contains N integers a<sub>i</sub> (1 ≤ a<sub>i</sub> ≤ 2). If a<sub>i</sub> equals 1, this means *Mike* solved problem number <sub>i</sub> first. If a<sub>i</sub> equals 2, this means Jack solved problem number <sub>i</sub> first.


### Output

Print “Mike” if Mike solved more problems faster than Jack, or print “Jack” if Jack solved more problems
faster than Mike. Otherwise, print “Tie”.  
 
![problem_2_io]({{ site.baseurl }}/images/BCPC/b.png)

### Réflexion

Le but de ce problème est de compter le nombre de '1' et de '2' dans une liste de N éléments composés uniquement de 1 et de 2.

- <span style="color:#e83e8c; background-color: #e4dcdc9e;">si N1 > N2 alors **Afficher("Mike")**</span>

- <span style="color:#e83e8c; background-color: #e4dcdc9e;">si N2 > N1 alors **Afficher("Jack")**</span>

- <span style="color:#e83e8c; background-color: #e4dcdc9e;">sinon **Afficher("Tie")**</span>



### SOLUTION PYTHON 3:

```py

import sys

sys.stdin = open("winner.in", "r")

N = input()

resultats = input().split()

N1 = resultats.count('1')

N2 = resultats.count('2')

if N1 > N2: print("Mike")

elif N2 > N1: print("Jack")

else: print("Tie")

```


## Problem D. Largest Number

### Sujet

One day, Mike was attending a lecture at his university, but he got bored so he stopped paying attention
to what his professor was saying.

His professor was smart and noticed that Mike wasn’t paying attention, so he challenged him with a
problem.

He wrote N digits on the board and asked him: what is the largest number that you make with these
digits?


### Input

The first line contains the N (1 ≤ N ≤ 104) the number of digits written on the board.

The second contains the N digits: Di (1 ≤ Di ≤ 9).
 

### Output

Print the largest number that can be formed by the given digits.
 
![problem_d_io]({{ site.baseurl }}/images/BCPC/d.png)

### Réflexion

Dans une liste de N chiffres on nous demande quel est le plus grand nombre que l'on peut former en les combinant. Vous convenez avec moi qu'il faut juste trier la liste par ordre décroissant.



### SOLUTION PYTHON 3:

```py

import sys

sys.stdin = open("number.in", "r")

N = input()

digits = list(input())

digits.sort(reverse = 1)

print(''.join(digits))

```

## Problem E. Matrix

### Sujet

You are given a grid A that has N rows and N columns.

Count the number of sub-grids of grid A such that the sub-grid has X rows and X columns, and if you
rotate this sub-grid 90 degrees to the right, it will remain unchanged.

### Input 

The first line of input has 2 integers: N and X (1 ≤ N ≤ 50) , (1 ≤ X ≤ N). The following N lines have N numbers: ai (0 ≤ ai ≤ 100).

### Output 

Print one integer, the answer to this problem.

![problem_e_io]({{ site.baseurl }}/images/BCPC/e.png)

### Réflexion

Ce problème présentait un **ENORME** pic de difficulté par rapport aux précédents. C'était le problème que j'ai le plus aimé, en plus nous étions la seule équipe à l'avoir réussi.

Pour ce problème, on avait en entrée une matrice carrée de d'ordre **N** et il fallait trouver le nombre de matrices carrées d'ordre **X** contenues dans cette dernière et dont la **rotation de 90 degrés** dans le sens horaire donne toujours la même matrice.

On cherche donc les matrices Mi dont <span style="color:#e83e8c; background-color: #e4dcdc9e;">**Rotation**(Mi) = Mi</span>.

Prenons l'exemple 1 et vérifions tout les matrices carrées d'ordre valides:

![m1]({{ site.baseurl }}/images/BCPC/r1.png)
![m2]({{ site.baseurl }}/images/BCPC/r2.png)
![m3]({{ site.baseurl }}/images/BCPC/r3.png)
![m4]({{ site.baseurl }}/images/BCPC/r4.png)
![m5]({{ site.baseurl }}/images/BCPC/r5.png)
![m6]({{ site.baseurl }}/images/BCPC/r6.png)
![m7]({{ site.baseurl }}/images/BCPC/r7.png)
![m8]({{ site.baseurl }}/images/BCPC/r8.png)
![m9]({{ site.baseurl }}/images/BCPC/r9.png)


Le plus dur était d'extraire les matrices d'ordre X de la matrice initiale. Pour le faire il faut repérer les cases <span style="color:#e83e8c; background-color: #e4dcdc9e;">M<sub>i,j</sub></span> où <span style="color:#e83e8c; background-color: #e4dcdc9e;">i + x ≤ N et j + x ≤ N</span>. Après cela il faut rajouter les:

<span style="color:#e83e8c; background-color: #e4dcdc9e;">**lignes[ i + k ][ j : j+x ]**</span> avec **K [0:x-1]**

La fonction de rotation, elle est assez simple, vous avez dû remarquer que les colonnes deviennent des lignes puis ont les inverse.

### SOLUTION PYTHON 3:

```py

import sys



def rotate(g, x):

    rotation=[]

    for i in range(x):
        a=[]
        for j in range(x):
            a.append(g[j][i]) # Transformation de colonne en ligne

        rotation.append(a[::-1]) # inversion

    return g == rotation # 1 si vrai 0 si faux
    
    

sys.stdin=open("matrix.in", "r")

n , x = map(int,input().split())

matrix=[]

for _ in range(n): matrix.append(input().split())

resultat = 0

for i in range(n-x+1):

    for j in range(n-x+1):

        mat=[]

        for k in range(x):

            mat.append(matrix[i+k][j:j+x])
        
        resultat += rotate(mat,x)


print(resultat)

```

## Problem F. Sequence

### Sujet

Nobody really likes long statements, so let’s get to the point.

Given a sequence of distinct numbers from 1 to N. There are 4 categories to classify the given sequence:

* Category 1: The sequence is increasing.
* Category 2: The sequence is decreasing.
* Category 3: The sequence is increasing then decreasing.
* Category 4: The sequence is decreasing then increasing.
    
It’s guaranteed that the given sequence belongs to one of the above categories.

### Input 

The first line of input consists one integer N (2 ≤ N ≤ 10<sup>3</sup>) - the length of the sequence.

The second line contains all numbers from 1 to N.

### Output 

Print the number of the category to which the sequence belongs.

![problem_f_io]({{ site.baseurl }}/images/BCPC/f.png)

### Réflexion

Il faut donner la catégorie d'une liste:

- si elle est dans l'ordre croissant alors <span style="color:#e83e8c; background-color: #e4dcdc9e;">Catégorie 1</span>

- si elle est dans l'ordre décroissant alors <span style="color:#e83e8c; background-color: #e4dcdc9e;">Catégorie 2</span>

Si elle n'est dans aucune dans ces deux catégories alors elle est forcément dans la catégorie 3 ou 4. Pour cela il faut comparer liste[0] et liste[1]:

- si liste[0] < liste[1] alors <span style="color:#e83e8c; background-color: #e4dcdc9e;">Catégorie 3</span>

- sinon <span style="color:#e83e8c; background-color: #e4dcdc9e;">Catégorie 4</span>



### SOLUTION PYTHON 3:

```py

import sys

sys.stdin=open("seq.in", "r")

n = input()

numbers = input().split()

tri = sorted(numbers)

if tri == numbers:

    print(1)

    sys.exit(0)

if tri == numbers[::-1]:

    print(2)

    sys.exit(0)

print(3 if numbers[0] < numbers[1] else 4)

```

## Problem G. Painting

### Sujet

One day, as George was on his way back home, he saw a painting in the street. He discovered that it was
a magical painting. The painting was divided into rows and columns like a grid. Each cell was initially
colored in white.

Here is the magic, when George touches a cell in the painting, it’s color and the color of its neighbors (if
found) changes. If it’s black, it changes to white and if it’s white it changes to black. The neighbors of a
cell are the cells that share a side with it.

Given the cells that George touched, you should expect the color of each cell.

### Input 

The first line contains three integers N, M and Q (1 ≤ N, M ≤ 1000),(1 ≤ Q ≤ 1000) - the number of
rows, number of columns and the number of cells George touched, respectively.

The next Q lines contain two integers X and Y (1 ≤ X ≤ N, 1 ≤ Y ≤ M) - the row and the column of
the cell George touched.

### Output 

Print the N lines, each line contains M integers separated by single space representing the grid after the
operations.

Print 1 if the cell is black and 0 if the cell is white.

![problem_g_io]({{ site.baseurl }}/images/BCPC/g.png)

### Réflexion

On nous donne une grille de taille N*M et lorsque l'on touche une case, elle et tous ses voisins changent de couleur.

Sachant que toutes les cases sont coloriées en blanc au début, on nous donne une série de cases qui ont été touchées et nous devons afficher l'état de la grille à la fin.

On considérer les cases comme des lampes, Si elles sont allumées(1) on les éteint(0) et vice-versa.

Supposons qu'on touche une case de coordonnées i, j;

- Si case[i][j] est allumée alors l'éteindre sinon l'allumer (Pour cela on utilise l'opérateur <span style="color:#e83e8c; background-color: #e4dcdc9e;">!</span> qui peut être considéré ici comme l'interrupteur)

- on répète la même oppération pour tous ses voisins que sont <span style="color:#e83e8c; background-color: #e4dcdc9e;">(i−1, j), (i+ 1, j), (i, j + 1) et (i, j −1)</span>


### SOLUTION C++:

```cpp

#include<bits/stdc++.h>


using namespace std;

bool colored[1001][1001];

int main ()
{


    ios_base::sync_with_stdio(false); cin.tie(NULL);

    freopen("paint.in", "r",stdin);

    memset(colored, 0 , sizeof(colored));

    int N,M,Q;

    scanf("%d %d %d", &N, &M, &Q);

    for(int i = 0; i < Q; i++)
    {
        int x, y;

        scanf("%d %d", &x, &y);

        colored[x][y]=!colored[x][y];

        
        colored[x-1][y] = !colored[x-1][y];

        colored[x+1][y] = !colored[x+1][y];

        colored[x][y+1] = !colored[x][y+1];

        colored[x][y-1] = !colored[x][y-1];
    }


    for (int i =1; i<=N; i++)
    {
        for(int j=1; j<=M; j++)
        {
            if( j<M)
            printf("%d ", colored[i][j]);
            else
            printf("%d", colored[i][j]);
        }
        puts("");
    }

}

```

## Problem K. Mango

### Sujet

“I wrote the word **Mango**, mom!”

“Oh, that’s impressive baby girl.”

Little Lama is learning the English alphabet, that’s why her parents decided to order her magnetic
alphabet so she can stick them on the fridge. To order the alphabet, Lama’s parents first tell the store
how much they want from the letter “a”, how much they want from letter “b”, how much they want from
letter “c”... and so on until letter “z”.

Lama wants to write down the string S, can you help her count how much they need from every letter of
the alphabet?

Also, can you sort the word S for Lama to make it easier for her to write?

### Input 

The first -and only- line of input has the string S (1 ≤ |S| ≤ 10<sup>5</sup>) - the word Lama wants to write.

### Output 

The first line should have 26 space-separated integers, each representing how much Lama needs from each
letter of the alphabet [a, b, c, d, e ....... y, z] to write the word S.

The second line of the output should have the string S2 - which is the sorted version of string S.

![problem_k_io]({{ site.baseurl }}/images/BCPC/k.png)
### Réflexion

Pour un mot qu'on nous donne, il faut afficher le nombre d'occurence de chaque lettre miniscule de l'alphabet puis afficher le mot trié.


### SOLUTION PYTHON 3:

```py

import sys
import string

sys.stdin=open("mango.in", "r")

s = input().lower()

for i in string.ascii_lowercase:
    print(s.count(i),'' if i != 'z' else '\n',end='')

print(''.join(sorted(list(s))))

```

## Problem K. Mango

### Sujet

Homos is a big boy now and he knows that his younger sister: Shambo, has just learnt about mathematical
operations. He decided to test her understanding using a little trick. Homos will give Shambo two numbers:
X and Y . He is going to let Shambo choose the number N, where:

<div style="text-align:center;">N = X + Y or N = X ∗ Y or N = X − Y</div>

Then, Homos will give Shambo exactly N cookies. Shambo loves cookies so much, so she wants to have
the maximum number of cookies she can get.

Help Shambo determine the value N.


### Input 

The first -and only- line of input has two integers: X and Y , (−10<sup>9</sup> ≤ X, Y ≤ 10<sup>9</sup>) - the two numbers
Homos will give to Shambo.

### Output 

Output a single number N - the maximum number of cookies Shambo can get.

![problem_l_io]({{ site.baseurl }}/images/BCPC/l.png)
### Réflexion

On nous donne deux entiers X et Y et nous devons donner le plus grand nombre N que l'on peut former à partir de ces deux nombres en utilisant:

- l'addition
- la multiplication
- la soustraction

La soustraction n'étant pas commutative, il faudra faire attention à vérifier <span style="color:#e83e8c; background-color: #e4dcdc9e;">X - Y</span> et <span style="color:#e83e8c; background-color: #e4dcdc9e;">Y - X</span>

On a donc:

<div style=" text-align: center;"><span style="color:#e83e8c; background-color: #e4dcdc9e;">N = max(X + Y, X * Y, X - Y, Y - X)</span></div>


### SOLUTION PYTHON 3:

```py

import sys

sys.stdin=open("trick.in", "r")

X , Y = map(int, input().split())

print(max(X + Y, X * Y, X - Y, Y - X))

```

Voilà nous sommes à la fin de cet article, j'espère qu'il vous aura plus. N'hésitez pas à le partager et à me suivre sur [facebook](https://www.facebook.com/Samir-Maoude-100925784983877?_rdc=1&_rdr) et [twitter](https://twitter.com/MaoudeSamir) pour être au courant de mes prochaines publications.
