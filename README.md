#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>
#include<conio.h>

#define TAM 200

struct PROJETO
{
	int codigo;
	char nome[100];
	char vacina[50];
	char cpf[40];
	char data[12];
	char numero_de_Lote[50];
};

int menu(){
	int num;
	system("cls");
	printf("1- Cadastrar Vacina\n 2 - Listar Aplicações\n 3 - Consultar por CPF\n 4 - Sair\n Opção: ");
	scanf("%d",&num);
	
	return num;
}
int main(){
	int num, cont = 0, aux,  i;
	struct PROJETO ficha[TAM];
	char cpfConsulta[40];
	
	setlocale(LC_ALL, "Portuguese");
	do{
		num = menu();
		switch(num){
			case 1:
				system("cls");
				
				if(cont <= 200){
					printf("Cadastro de Vacina: \n");
					
					printf("Codigo: %d \n", (cont));
					fflush(stdin);
					printf("Informe o nome: ");	
					gets(ficha[cont].nome);
					fflush(stdin);								
					
					printf("Informe o cpf: ");	
					gets(ficha[cont].cpf);
					fflush(stdin);
					
					printf("Informe o nome da Vacina: ");	
					gets(ficha[cont].vacina);
					fflush(stdin);
					
					printf("Informe a Data: ");	
					gets(ficha[cont].data);
					fflush(stdin);
					
					printf("Informe o Lote: ");	
					gets(ficha[cont].numero_de_Lote);
					fflush(stdin);
					
					printf("\n Cadastro Realizado com Sucesso..\n");
					ficha[cont].codigo = cont;
					cont++;
					
					
				}else{
					printf("\n Base de Dados cheia: \n");
					
				}
				system("Pause");
				system("cls");			
			break;
			case 2:
				system("cls");
				if(cont > 0){
					for(i = 0; i < cont; i++){
						printf("Código: %d", ficha[i].codigo);
						printf("\n Nome: %s", ficha[i].nome);
						printf("\n Cpf: %s", ficha[i].cpf);
						printf("\n Vacina: %s", ficha[i].vacina);
						printf("\n Data: %s", ficha[i].data);
						printf("\n Numero do Lote: %s", ficha[i].numero_de_Lote);
						printf("\n ------------------------------------------------- \n");
					}
				}else{
					printf("\n Lista de Cadastro Vazio..");
				}
				system("Pause");
				system("cls");
				
			break;
			
			case 3:
				system("cls");
				getchar();
				printf("Informe o cpf para Consultar: ");	
				gets(cpfConsulta);
				fflush(stdin);
				if(cont > 0){
					aux = 0;
					for(i = 0; i < cont; i++){
						if(strcmp(cpfConsulta, ficha[i].cpf) == 0){
							aux = 1;
							printf("Código: %d", ficha[i].codigo);
							printf("\n Nome: %s", ficha[i].nome);
							printf("\n Cpf: %s", ficha[i].cpf);
							printf("\n Vacina: %s", ficha[i].vacina);
							printf("\n Data: %s", ficha[i].data);
							printf("\n Numero do Lote: %s", ficha[i].numero_de_Lote);
							printf("\n ====================================== \n");
						}
					}
					if(aux == 0){
						printf("Cpf: %s, não foi encontrado nenhum Registro \n", cpfConsulta);
					}
				}else{
					printf("\n Lista de Cadastro Vazio..");
				}
				system("Pause");
				fflush(stdin);
				getchar();
				system("cls");
			break;
			
			case 4:
				printf("\n Fim...");
			break;
			
			default:
				printf("\n Opção Inválida");
			break;
			
		}
	}while(num != 4);
	
	return 0;
}
