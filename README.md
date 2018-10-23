# Jogo-da-Velha#include <stdio.h>
#include <stdlib.h>

int tabuleiro(char jogo[9]) {
	system("cls");
	printf("--- JOGO DA VELHA COM VETOR ---\n\n");
	printf("\t %c | %c | %c \n", jogo[0], jogo[1], jogo[2]);
	printf("\t-----------\n");
	printf("\t %c | %c | %c \n", jogo[3], jogo[4], jogo[5]);
	printf("\t-----------\n");
	printf("\t %c | %c | %c \n", jogo[6], jogo[7], jogo[8]);

	return 0;
}

int main()
{
	char casa[9] = { '1','2','3','4','5','6','7','8','9' };
	char res;
	int cont_jogada, jogada, vez = 0, limpar;

	do {
		cont_jogada = 1;
		for (limpar = 0; limpar <= 8; limpar++)
			casa[limpar] = ' ';
		do {
			tabuleiro(casa);
			if (vez % 2 == 0) {
				printf("\nJogador X\n");
			}
			else {
				printf("\nJogador O\n");
			}
			printf("\nDigite a casa para marcar[1-9]\n");
			scanf_s("%i", &jogada);
			if (jogada < 1 || jogada > 9) {
				jogada = 0;
			}
			else if (casa[jogada - 1] != ' ') {
				jogada = 0;
			}
			else {
				if (vez % 2 == 0) {
					casa[jogada - 1] = 'X';
				}
				else {
					casa[jogada - 1] = 'O';
				}
				cont_jogada++;
				vez++;
			}
			if (casa[0] == 'X' && casa[1] == 'X' && casa[2] == 'X') { cont_jogada = 11; }
			if (casa[3] == 'X' && casa[4] == 'X' && casa[5] == 'X') { cont_jogada = 11; }
			if (casa[6] == 'X' && casa[7] == 'X' && casa[8] == 'X') { cont_jogada = 11; }
			if (casa[0] == 'X' && casa[3] == 'X' && casa[6] == 'X') { cont_jogada = 11; }
			if (casa[1] == 'X' && casa[4] == 'X' && casa[7] == 'X') { cont_jogada = 11; }
			if (casa[2] == 'X' && casa[5] == 'X' && casa[8] == 'X') { cont_jogada = 11; }
			if (casa[0] == 'X' && casa[4] == 'X' && casa[8] == 'X') { cont_jogada = 11; }
			if (casa[2] == 'X' && casa[4] == 'X' && casa[6] == 'X') { cont_jogada = 11; }

			if (casa[0] == 'O' && casa[1] == 'O' && casa[2] == 'O') { cont_jogada = 12; }
			if (casa[3] == 'O' && casa[4] == 'O' && casa[5] == 'O') { cont_jogada = 12; }
			if (casa[6] == 'O' && casa[7] == 'O' && casa[8] == 'O') { cont_jogada = 12; }
			if (casa[0] == 'O' && casa[3] == 'O' && casa[6] == 'O') { cont_jogada = 12; }
			if (casa[1] == 'O' && casa[4] == 'O' && casa[7] == 'O') { cont_jogada = 12; }
			if (casa[2] == 'O' && casa[5] == 'O' && casa[8] == 'O') { cont_jogada = 12; }
			if (casa[0] == 'O' && casa[4] == 'O' && casa[8] == 'O') { cont_jogada = 12; }
			if (casa[2] == 'O' && casa[4] == 'O' && casa[6] == 'O') { cont_jogada = 12; }

		} while (cont_jogada <= 9);
		tabuleiro(casa);
		if (cont_jogada == 10) {
			printf("\nJogo Empatado\n");
		}if (cont_jogada == 11) {
			printf("\nVencendor o jogador X\n");
		}if (cont_jogada == 12) {
			printf("\nVencendor o jogador O\n");
		}

		printf("\nVamos jogar novamente?[S-N]\n");
		scanf_s("%s", &res);
	} while (res == 's',1);

	system("pause");
	return 0;
}
