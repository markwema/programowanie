#Zajęcia z dnia 2.03.2013
```c

int main() {
  printf(("Witaj świecie\n";
}

```

Program obliczajacy pole o obwod kola

```c
#include <stdio.h>
#include <math.h>
int main(){
 double r;
 const double pi=M_PI;
 puts("Podaj promien kola\n");
 scanf("%lf",&r);/*  czyta wartosc promienia z kalwiatury */
 printf("Pole wynosi S=%lf, a dlugosc L=%lf",pi*r*r,2*pi*r); 
 
 getchar();/* enter ze scanf() w buforze */
 getchar();
 return 0;
}
```

Przeliczanie tamperatury Fahrenheita->Celsius

```c
#include <stdio.h>

int main(){
 int fahr,celsius; /* deklaracja temperatur */
 int lower, upper, step; /* zakres temperatur i krok */
 lower=0;
 upper=300;
 step=20;
 fahr=lower; /* instrukcja podstawienia */
 while(fahr <= upper){
            celsius=5*(fahr-32)/9;
            printf("%d \t %d\n",fahr,celsius);
            fahr=fahr+step;}
            getchar();
            return 0;
            }
```
```c
#include <stdio.h>

int main(){
double fahr,celsius; /* deklaracja temperatur */
 int lower, upper, step; /* zakres temperatur i krok */
 lower=0;
 upper=300;
 step=20;
 fahr=lower; /* instrukcja podstawienia */
 while(fahr <= upper){
            celsius=5*(fahr-32)/9;
            printf("%5.1lf \t %7.2lf\n",fahr,celsius);
            fahr=fahr+step;}
            getchar();
            return 0;
            }
```
Kolejna wersja konwersji temperatur z użyciem deklaracji preprocesora
```c
#include <stdio.h>
#define LOWER 0
#define UPPER 300
#define STEP 20


int main(){
int fahr;
for(fahr=LOWER;fahr <= UPPER;fahr=fahr+STEP)
printf("%d3d %6.1lf\n",fahr,(5.0/9.0)*(fahr-32.0));
getchar();
return 0;
}
```

Ciąg Fibonaciego

```c
#include <stdio.h>


int main(){
int n1,n2,n3; /*kolejne wyrazy ciagu */
int n; /* numer wyrazu*/
int i; /* licznik */
    do{puts("Podaj numer wyrazu (co najmniej 3):");
         scanf("%d",&n);
         }
         while(n<3);
         n1=n2=1;  /* dwa pierwsze wyrazy ciągu*/
         i=2;
         while(i++<n) /*uwaga, musi być n>2*/
         {
                      n3=n1+n2;
                      n1=n2;
                      n2=n3;
                      }     
     printf("Wyraz o numerze %d ma wartosc %d:",n,n3);       
getchar();
getchar();
return 0;
}
```

Rysowanie choinki

```c
#include <stdio.h>


#define znak '*' /*znak wypełniania*/
int main(){
int lbwier; /*całkowita liczba wierszy*/
int lw;/* licznik wierszy*/
int lodst; /*liczba odstępów poprzedzających gwiazdkę*/
int j;
printf("ile wierszy?");
scanf("%d",&lbwier);
for(lw=0;lw<lbwier;lw++)
{ lodst=lbwier-lw-1;
for(j=0;j<lodst;j++)putchar(' ');
for(j=0;j<2*lw+1;j++)putchar(znak);
putchar('\n');
}
getchar(); getchar();
}
```

Zadanie 1
```c
#include <stdio.h>



int main(){
int i;
for(i=0;i<24;i++)
printf("%d ,", i);
putchar('\n');
i=0;
while(i<24){
            printf("%d ,", i);
            i++;}
putchar('\n');
i=0;
do{printf("%d ,", i);
i++;
}
while(i<24);     
getchar();
}
```

Zadanie 2.

```c
#include <stdio.h>

int main(){
    double start=-3.6;
    double end=7.5;
    double krok=0.5;
    double slad;
    for(slad = start;slad <= end;slad = slad+krok) printf("%lf \t",slad);
    slad=start;
    while(slad<=end){
              printf("%lf \t",slad);
              slad=slad+krok;
              }       
              getchar();        
}
```

Zadanie 3.

```c
#include <stdio.h>

int main(){
    double liczba;
    int n=0;
    double suma=0;
    int licznik=0;
    puts("Podaj ile liczb wczytasz:\n");
    scanf("%d",&n);
    while(licznik<n)
    {    scanf("%lf",&liczba);
         licznik++;
         suma+=liczba;
         }
         printf("Suma = %lf \t , a srednia= %lf",suma,suma/n);
         getchar();
         getchar();        
}
```

Zadanie 4

```c
#include <stdio.h>

int main(){
    unsigned int n;
    puts("Podaj ile liczb uwzglednic:\n");
    scanf("%d",&n);
    int i;
  for(i=1;i<=n;i++)printf("%d \t %d\n",i*i,i*i*i);
   while(i<=n)
    {    printf("%d \t %d\n",i*i,i*i*i);
         i++;
         }
        i=1;
    do{printf("%d \t %d\n",i*i,i*i*i);
         i++;}
         while(i<=n);
    
         getchar();
         getchar();        
}
```
## Wskaźniki
### Przykłady
deklaracja
```c
int *x;
```
mówi, że x jest adresem (wskaźnikiem) do zminnej typu int;
Wywołanie
```c
*x;
```
wywołuje zawrtość komórki pamięci na którą wskazuje **x**,
a napis
```c
&x
```
wyłuskuje adres zmiennej **x**
Wskaźniki mogą być do typów: **int, double, char**
oraz do funkcji itd

# Funkcje

### Przekazywanie parametrów

Gdy wywołujemy funkcję, wartość argumentów, z którymi ją wywołujemy, jest kopiowana do funkcji. Kopiowana -
to znaczy, że nie możemy normalnie zmienić wartości zewnętrznych dla funkcji zmiennych. Formalnie mówi się, że
w C argumenty są przekazywane przez wartość, czyli wewnątrz funkcji operujemy tylko na ich kopiach.
Możliwe jest modyfikowanie zmiennych przekazywanych do funkcji jako parametry - ale do tego w C potrzebne są
wskaźniki.
### Wskaźniki na funkcje
Szczególnym rodzajem wskaźnika jest wskaźnik na funkcję, który w uproszczeniu
można traktować jak adres początku tej funkcji. Równocześnie sama nazwa funkcji
ma wartość adresu początku kodu stanowiącego obraz tej funkcji w pamięci.
Wywołanie pewnej funkcji poprzez wskaźnik p na tę funkcję można dokonać
używając wyrażenia:
```c
( *p ) ( lista_argumentów )
void (*p1)();
 //Wskaznik na funkcje bez
//argumentow i nie zwracajaca
//wartosci
int (*p2)(int,char);
 //Wskaznik na funkcje o argumentach
//int i char, zwracajaca int
int *(*p3)(int);
 //Wskaznik na funkcje o argumencie
//int, zwracajaca wskaznik na int
double (*(*p4)(int))(char); //Wskaznik na funkcje o argumencie
//int, zwracajaca wskaznik na
//funkcje o argumencie char, ktora
//zwraca double

```
__Uwaga:__ Operacje na wskaźnikach na funkcje podlegają dodatkowemu ograniczeniu:
Na wskaźnikach na funkcje nie można wykonywać operacji arytmetycznych.

### Wskaźniki na tablice i tablice wskaźników
Wskaźnik na tablicę należy odróżniać od wskaźnika na początkowy element tej
tablicy. Podstawową zasadą, którą należy zawsze stosować, jest reguła działania
operatora wyłuskania:
Zastosowanie operatora wyłuskania do wskaźnika na pewien
obiekt daje w rezultacie ten obiekt.
