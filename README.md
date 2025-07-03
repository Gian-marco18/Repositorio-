#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include<windows.h>

#define VERDE "\033[0;32m"
#define ROJO "\033[0;31m"
#define RESET "\033[0m"


int main (int argc, char *argv[]){

    int i;
	int cant;
	int longitud=0;
	char buscarAutor[15];
    int encontrado = 0;
    
    
	printf("Ingrese la Cantidad de Libros a Registrar: ");
	scanf("%d", &cant);
	
	char tit[cant][15];
	char aut[cant][15];
	char gen[cant][15];
	char isbn[7][11];
	int stock[cant];
	float precio[cant];
	float ganancias[cant];
	
	for(i=0;i<=cant-1;i++){
		
		printf("Ingrese Nombre del Libro:\n ");
		scanf(" %[^\n]s", &tit[i]);
		
		printf ("\nIngrese el Nombre del Autor:\n ");
		scanf (" %[^\n]s", &aut[i]);
		
		printf ("\nIngrese el Genero:\n ");
		scanf (" %[^\n]s", &gen[i]);
		
		printf ("\nIngrese la Cantidad Disponible en Inventario:\n ");
		scanf (" %d", &stock[i]);
		
		printf ("\nIngrese el Precio del Libro:\n ");
		scanf (" %f", &precio[i]);
		
		ganancias[i] = stock[i] * precio[i];
		
		do{
			printf("Ingrese el ISBN:\n");
		    scanf(" %[^\n]s", &isbn[i]);
		    
		    longitud = strlen(isbn[i]);
		}while(longitud !=10);
		
		
		system("CLS");
		
	}
	
		printf("LIBRO\t  AUTOR\t  GENERO\tISBN\t  DISPONIBLE\t  PRECIO\t GANANCIA\n");
	
	
	for(i = 0; i <= cant-1; i++) {
	  	if (ganancias >= 0){
		  printf("%s\t  %s\t  %s\t  %s\t  %d\t          %.2f\t        "VERDE" %.2f\n"RESET" ", tit[i], aut[i], gen[i], isbn[i], stock[i], precio[i], ganancias[i]);

	  	}else if (ganancias <= 0){
		  		  
	  	  printf("%s\t  %s\t  %s\t  %s\t  %d\t          %.2f\t        "ROJO" %.2f\n"RESET" ", tit[i], aut[i], gen[i], isbn[i], stock[i], precio[i], ganancias[i]);
	      }
	    }
    
	  
	   printf("\nIngrese el autor del libro que desea buscar: ");
    scanf(" %[^\n]s", buscarAutor);

    printf("\nResultados de la busqueda por autor '%s':\n", buscarAutor);
    for (i = 0; i < cant; i++) {
        if (strcmp(aut[i], buscarAutor) == 0) {
            printf ("Nombre:%s Autor:%s Genero:%s ISBN:%s Disponible:%d Precio:%.2f Ganancias:%.2f\n", tit[i], aut[i], gen[i], isbn[i], stock[i], precio[i], ganancias[i]);
            encontrado = 1;
        }
    }

    if (!encontrado) {
        printf("No se encontraron libros del autor '%s'.\n", buscarAutor);
    }
	  
	  
	return 0;
	
	
}

