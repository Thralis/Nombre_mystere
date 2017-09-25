# Nombre_mystere
mini jeu console en C

#include <stdio.h>

#include <stdlib.h>

#include <time.h>


int main ( int argc, char** argv )

{
    int nombreEntre = 0, choixJoueur = 0, choixDifficulter = 0, nombreDeCoups = 0,nombreMaximum = 0, MIN = 1;
    unsigned long nombreMystere = 0;


    // generation du nombre aleatoire //


    srand(time(NULL));


    // on fait le menu du jeux, avec la selection de nombre de joueur //


    printf("\t\t Bienvenue sur le nombre mystere!\n\n");
    printf("Selectionner le nombre de joueur:\n");
    printf("1 joueur:\t\t2 joueurs:\n");
    scanf("%d", &choixJoueur);
    printf("\n");


    // on programme des conditions pour les multiples choix possibles //



    if (choixJoueur == 1)
    {


        printf("vous avez selectionné 1 joueur.\n");
        printf("\n   Selectionner le niveau de difficulter:\n");
        printf("1.Facile:\t2.Moyen:\t3.Difficile:\n");
        scanf("%d", &choixDifficulter);
        printf("\n");


    // on programme les differents choix de difficulter voulu //


            if(choixDifficulter == 1)
            {
                printf("vous avez choisi de jouer en facil.\n\n");

                nombreMaximum = 100;
                nombreMystere = (rand() % (nombreMaximum - MIN +1)) + MIN;
            }

            else if(choixDifficulter == 2)
            {
                printf("vous avez choisi de jouer en moyen.\n\n");

                nombreMaximum = 1000;
                nombreMystere = (rand() % (nombreMaximum - MIN +1)) + MIN;
            }

            else if(choixDifficulter == 3)
            {
                printf("vous avez choisi de jouer en difficile.\n\n");

                nombreMaximum = 10000;
                nombreMystere = (rand() % (nombreMaximum - MIN +1)) + MIN;
            }

            else
            {
                printf("vous avez decidé de quitter le jeu!\n");
                return 0;
            }
    }


    /* si le joueur selectionne 2 joueur il devra choisir le nombre
       a faire trouver au 2 eme joueur */


     else if (choixJoueur == 2)
    {
        nombreMystere = 100001;


    /* on fait une boucle pour que le nombre mystere ne depasse pas les 100 000 et on vide le cache
       pour ne pas crée de boucle infinni en cas de rentré de lettre par le deuxieme joueur */


        while (nombreMystere > 100000)
        {
            printf("vous avez choisi le mode 2 joueurs\n\n");
            printf("joueur 2 choisissez votre nombre mystere!\n");
            printf("le nombre mystere ne dois pas depasser 100 000\n");
            fflush(stdin);
            scanf("%ld", &nombreMystere);
            system("cls");
        }
    }

    else
    {
       printf("vous avez decidé de quitter le jeu!\n");
       return 0;
    }


    /* la boucle du programme est concu pour ce repeter tant que
       le joueur n'as pas trouve le nombre mystere */

    do
    {
        printf("quel est le nombre mystere?");
        fflush(stdin);
        scanf("%d", &nombreEntre);
        nombreDeCoups++;

    if (nombreMystere < nombreEntre)
        printf("c'est moin!\n\n");

    else if (nombreMystere > nombreEntre)
        printf ("c'est plus!\n\n");

    else
        printf("felicitations, vous avez trouvé le nombre mystere en %d coups!\n\n", nombreDeCoups);

    }while (nombreEntre != nombreMystere);

    return 0;
}
