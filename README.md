//# Array_Functions
//In this repository i wrote some easy Functions for Arrays

include <stdio.h>
#include <stdlib.h>
#define DIM 10

void show_menu();
void menu();

int greaterThan(int *a);
int member(int *a, int k);
int largest(int *a);
int *remove1(int *a, int k);
int ordering(int *a);
int *reverse1(int *a);
void printVector(int *a);

int main()
{
    show_menu();

    menu();

    return 0;
}

void show_menu()
{
    printf("Premere un tasto per scegliere una funzione:\n\n");
    printf("1.greaterThan (Trovare quanti numeri sono maggiori di un certo intero k)\n\n");
    printf("2.member (Stabilisce se un numero k appartiene al vettore inserito)\n\n");
    printf("3.largest (Trova il numero piu' grande nel vettore)\n\n");
    printf("4.remove1 (Rimuove dal vettore un numero inserito dall'utente)\n\n");
    printf("5.ordering\n\n");
    printf("6.reverse1 (Inverte il vettore inserito)\n\n");
    return;
}

void menu()
{
    int *a;
    int k;

    a =(int*)malloc(DIM*sizeof(int));

    *(a + 0) = 2;
    *(a + 1) = 23;
    *(a + 2) = 11;
    *(a + 3) = 9;
    *(a + 4) = 1150;
    *(a + 5) = 8;
    *(a + 6) = 41;
    *(a + 7) = 11;
    *(a + 8) = 90;
    *(a + 9) = 22;

    printf("Il vettore dato e':\n");

    int i;
    i = 0;
    for(i = 0; i < DIM; i++){
        printf(" %d ", a[i]);
    }

    printf("\n\n");

    int scelta_utente;
    scanf("%d", &scelta_utente);

    if(scelta_utente == 1){
        printf("\n Inserire un numero intero k: ");
        k = greaterThan(a);
        printf("\nNumero interi maggiori di k nel vettore: %d\n", k);
    }else if(scelta_utente == 2){
                printf("\n Inserire un numero intero k: ");
                k = member(a, k);
                printf("Se k appartiene al vettore 1, altrimenti 2: %d\n", k);
            }else if(scelta_utente == 3){
                        k = largest(a);
                        printf("Il numero piu' grande nel vettore e': %d\n", k);
                    }else if(scelta_utente == 4){
                                printf("\n Inserire un numero intero k: ");
                                scanf("%d", &k);
                                a = remove1(a, k);
                                printVector(a);
                            }else if(scelta_utente == 5){
                                    //k = ordering(a);
                                    printf("k uguale 0 vettore è in ordine crescente, se ordine decrescente 1, altrimenti 2: %d", k);
                                    }else if(scelta_utente == 6){
                                               a = reverse1(a);
                                               printf("Il vettore invertito e':\n");
                                               printVector(a);
                                            }
    return 0;
}

int greaterThan(int *a)
{

int k;
int temp = 0;
scanf("%d", &k);
int i = 0;
for(i = 0; i < DIM; i++)
{
    if(k < a[i]){
    temp++;
    }
}
return temp;
}

int member(int *a, int k)
{
    scanf("%d", &k);
    int temp1 = 0;
    int temp;
    int i;
    for(i = 0; (i < DIM && temp1 != -1); i++){
        if(k == a[i]){
        temp = 1;
        temp1 = -1;
        }else
            {
            temp = 2;
            }
}
return temp;
}

int largest(int *a)
{
 int temp;
 int i;
 temp = a[0];
 for(i = 0; i < DIM-1; i++)
 {
    if(a[i] > temp)
    {
        temp = a[i];
    }
 }
return temp;
}

int* remove1(int *a, int k)
{
    int temp;
    int temp1;
    int i = 0;
    temp = a[0];
    for(i = 0; (i < DIM && temp1 != -2); i++){
        if(k == a[i]){
         temp = i;
         temp1=-2;
        }

    }
    if(temp1 == -2){
    int j;
    j = 0;
    for(j = temp; j < DIM; j++){
        a[j] = a[j+1];
        if(a[j] == a[DIM-1])
        {
            a[DIM-1] = 0;
        }
        }
    }
return a;
}

/*
int ordering(int *a)
{
    int temp;
    int temp1;
    int i;
    temp = a[0];
    for(i = 0; i < DIM; i++){
        if(temp < a[i]){
            temp = a[i];
            temp1 = 0;
        }else if(temp > a[i]){
                temp = a[i];
                temp1 = 1;
            }else{
                    temp1 = 2;
                }
    }
    return temp1;
}
*/

int *reverse1(int *a)
{
    int j;
    int i;
    int *temp;
    temp = (int*)malloc(DIM*sizeof(int));
    for((j = DIM-1, i = 0); j!=-1; (j--, i++)){
        temp[i] = a[j];
    }
    return temp;
}


void printVector(int *a)
{
    int i;
    i = 0;
    for(i = 0; i < DIM; i++){
        printf(" %d ", a[i]);
    }
    return;
}
