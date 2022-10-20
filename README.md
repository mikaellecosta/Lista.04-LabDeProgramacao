<p align="center">
  <a href="#questão-1">1</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-2">2</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-3">3</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-4">4</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-5">5</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-6">6</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-7">7</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-8">8</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-9">9</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-10">10</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
</p>

# 📚 Lista 04 - Programação em C
Lista de exercícios submetida na cadeira de Laboratório de Programação.

## Questão 1:
Escreva um programa que adicione dois números usando ponteiros. Além do valor da soma, imprima
também o endereço de memória onde o valor resultante dessa soma está armazenado.

``` c
#include <stdio.h>
void soma(int *x, int *y, int *s);

int main() {
  int a, b, s;
  int *px = &a, *py = &b, *ps = &s;
  
  scanf("%d %d", &a,&b);
  soma(&a,&b,&s);
  
  // scanf("%d %d", px, py);
  // soma(px, py, ps);
  
  printf("%d + %d = %d",a, b, s);
  return 0;
}

void soma(int *x, int *y, int *s){
  *s = *x + *y;  
}
```

## Questão 2:
Escreva um programa que troque o valor de dois números utilizando ponteiros.

``` c
#include <stdio.h>
void troca(int *x, int *y, int *temp);

int main() {
  int a, b, temp;
  int *x = &a, *y = &b, *ptemp = &temp;

  printf("X e Y: ");
  scanf("%d, %d", x, y);
  troca(x,y,ptemp);
  printf("Após a troca: X = %d e Y = %d", a, b);
  return 0;
}

void troca(int *x, int *y, int *temp){
  *temp = *x;
  *x = *y;
  *y = *temp;
}
```

## Questão 3:
Escreva um programa que solicite iterativamente um numero do usuario e imprima sempre o menor valor fornecido. Crie um criterio para finaliza ̧cao do programa. Utilize ponteiros.

``` c
#include <stdio.h>

int main() {
  int num, menor;
  int *pnum=&num, *pmenor=&menor;
  
  for (int i = 0; ; i++){
    scanf("%d",pnum);
    
    if (num == 0){
      break;
   }
    
    if (i == 0){menor = num;}
      if(num < menor){
        menor = num;
      }
  }
    printf("Menor número --> %d",menor);

  return 0;
}
```

## Questão 4:
Escreva um programa que leia um vetor do usuario e imprima seus valores e seus enderecos. Teste o vetor com tipos de dados diferentes, analise os endere ̧cos. O que voce observou?
``` c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void printv(float *pv, unsigned int qnt);

int main() {
  int qnt, i;
  float *v;
  
  printf("Quantidade do vetor: ");
  scanf("%d",&qnt);
  v = calloc(qnt, sizeof(float)); 
  
  srand(time(NULL));
  
  for (i = 0; i < qnt; i++){
      v[i] = rand() % 100;
  }
  system("clear");
  printv(v, qnt);

  return 0;
}

void printv(float *pv, unsigned int qnt){
  for (int i = 0; i < qnt; i++){
    printf("end = [%p] --> valor = %0.2f\n",pv+i, *(pv+i));
  }
}
```

## Questão 5:
Escreva um programa que encontre o tamanho de uma string fornecida. Utilize ponteiros.
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define QNT 1000
char keyboard[BUFSIZ];

void setbuf();
void getinput(char *buff, int size);
void contar(char *qntword, int qnt);

int main() {
  char word[QNT];
  int *count=NULL;
  getinput(word, QNT);
  word[strcspn(word, "\n")] = 0;
  contar(word, *count);

  printf("A palavra %s tem %d caracteres!",word,*count);
  return 0;
}

void contar(char *qntword, int qnt) {
  while ( *qntword != '\0' ) { 
    qnt++ ;
    qntword++ ;
    }  
  }

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```

## Questão 6:
Escreva um programa que copie uma string para outra usando ponteiros.
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define QNT 1000
char keyboard[BUFSIZ];

void setbuf();
void getinput(char *buff, int size);
void contar(char *qntword, int qnt);
// void cop(char *um, char *dois, int tam);

int main() {
  char word[QNT], word2[QNT], *p, *q;
  int *count=NULL;
  p = word;
  q = word2;
  getinput(word, QNT);
  word[strcspn(word, "\n")] = 0;
  contar(word, *count);

  printf("A palavra %s tem %d caracteres!\n\n",word,*count);

  for (int i = 0; i < strlen(word); i++){
    q++;
    q = p;
  }
  printf("Palavra 1 = %s\nPalavra 2 = %s",p,q);
  return 0;
}

void contar(char *qntword, int qnt) {
  while ( *qntword != '\0' ) { 
    qnt++ ;
    qntword++ ;
    }  
  }

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}

// void cop(char *primeira, char *segunda, int tam){
//   for (int i = 0; i < strlen(primeira); i++){
//     segunda++;
//     segunda = primeira;
//   }
//    }
```

## Questão 7:
Escreva um programa que concatene duas strings utilizando ponteiros.
``` c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define QNT 1000
char keyboard[BUFSIZ];

void setbuf();
void getinput(char *buff, int size);
void concat(char *word1, char *word2, char *pconcat);

int main() {
  char word1[QNT],word2[QNT];
  char *pconcat = (char*) malloc(((int)strlen(word1) + (int)strlen(word2)+1)*sizeof(char));
  
  getinput(word1, QNT);
  word1[strcspn(word1, "\n")] = 0;
  getinput(word2, QNT);
  word2[strcspn(word2, "\n")] = 0;

  concat(word1, word2, pconcat);
  printf("%s", pconcat);
  
  return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}

void concat(char *word1, char *word2, char *pconcat){
  while(*word1){ 
  *pconcat = *word1;
  pconcat += 1;
  word1 += 1;
  }
  
while (*word2){ 
  *pconcat = *word2;
  pconcat += 1;
  word2 += 1;
  }
  
*pconcat = '\0';
}
```

## Questão 8:
Escreva um programa que busque um caracter fornecido em uma string utilizando ponteiros.
``` c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define QNT 1000
char keyboard[BUFSIZ];

void setbuf();
void getinput(char *buff, int size);
char *search(char *word, int caractere);

int main() {
  char word[QNT];
  char caracter;
  
  getinput(word, QNT);
  word[strcspn(word, "\n")] = 0;
  setbuf(stdin, keyboard);
  scanf("%c",&caracter);
  
  search(word, caracter);

  char *teste = search(word, caracter);
  
  if (teste == NULL){
    printf("%s não possui %c",word,caracter);
  }
  else{
    printf("%s possui %c",word,caracter);
  }
  return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}

char *search(char *word, int caractere){
   while(*word != '\0'){
     if(caractere == *word) return (char *) word;
       word++;
   }
  return NULL;
}
```

## Questão 9:
Implemente o método de ordenação bolha utilizando ponteiros.
``` c
#include <stdio.h>
#include <stdlib.h>
#define TAM 3

void bubblesort(int*, int);
void geravetor(int*, int);
void printvetor(int*, int);
int main(void){
  int v[TAM];
  geravetor(v, TAM);
  system("clear");
  printf("\nVetor inserido: \n");
  printvetor(v, TAM);
  
  bubblesort(v, TAM);
  printf("\nVetor ordenado: \n");
  printvetor(v, TAM);
    
  return 0;
}

void geravetor(int *vet, int tam){
  printf("\nInforme a vetor\n");
  for(int i = 0; i < tam; i++){
    printf("%dº valor = ", i+1);
    scanf("%d", (vet + i));
    }
  }

void bubblesort(int *vet, int tam){
  for(int i = 0; i < tam-1; i++){
    for(int j = i+1; j < tam; j++){
       if(*(vet + j) < *(vet + i)){
         *(vet + i) ^= *(vet + j);
         *(vet + j) ^= *(vet + i);
         *(vet + i) ^= *(vet + j);
          }
        }
      }
  }

void printvetor(int *vet, int tam){
    printf("[");
    for(int i = 0; i < tam; i++)
        printf(" %d ", *(vet + i));
    printf("]\n");
}
```

## Questão 10:


``` c

```










