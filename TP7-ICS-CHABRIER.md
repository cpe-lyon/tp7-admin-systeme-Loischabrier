Loïs CHABRIER

# _TP 7 - Boot, services et processus / Tâches d’administration (2)_

## Exercice 1. Personnalisation de GRUB


<span style='color:red'>1.</span> Commencez par changer l’extension du fichier /etc/default/grub.d/50-curtin-settings.cfg s’il
est présent dans votre environnement (vous pouvez aussi commenter son contenu).


<span style='color:red'>2.</span> Modifiez le fichier /etc/default/grub pour que le menu de GRUB s’affiche pendant 10 secondes ;
passé ce délai, le premier OS du menu doit être lancé automatiquement.


<span style='color:red'>3.</span> Lancez la commande update-grub


<span style='color:red'>4.</span> Redémarrez votre VM pour valider que les changements ont bien été pris en compte


<span style='color:red'>5.</span> On va augmenter la résolution de GRUB et de notre VM. Cherchez sur Internet le ou les paramètres
à rajouter au fichier grub.


<span style='color:red'>6.</span> On va à présent ajouter un fond d’écran. Il existe un paquet en proposant quelques uns : grub2-splash-images (après installation, celles-ci sont disponibles dans /usr/share/images/grub).


<span style='color:red'>7.</span> Il est également possible de configurer des thèmes. On en trouve quelques uns dans les dépôts (grub2-themes-*). Installez-en un.


<span style='color:red'>8.</span> Ajoutez une entrée permettant d’arrêter la machine, et une autre permettant de la redémarrer.


<span style='color:red'>9.</span> Configurer GRUB pour que le clavier soit en français


## Exercice 2. Noyau

<span style='color:red'>1.</span> Commencez par installer le paquet build-essential, qui contient tous les outils nécessaires (compi-
lateurs, bibliothèques) à la compilation de programmes en C (entre autres).


<span style='color:red'>2.</span> Créez un fichier hello.c contenant le code suivant :


<span style='color:red'>3.</span> Créez également un fichier Makefile :


<span style='color:red'>4.</span> Compilez le module à l’aide de la commande make, puis installez-le à l’aide de la commande make
install.


<span style='color:red'>5.</span> Chargez le module ; vérifiez dans le journal du noyau que le message ”La fonction init_module() est
appelée” a bien été inscrit, synonyme que le module a été chargé ; confirmez avec la commande lsmod.


<span style='color:red'>6.</span> Utilisez la commande modinfo pour obtenir des informations sur le module hello.ko ; vous devriez
notamment voir les informations figurant dans le fichier C.


<span style='color:red'>7.</span> Déchargez le module ; vérifiez dans le journal du noyau que le message ”La fonction cleanup_module()
est appelée” a bien été inscrit, synonyme que le module a été déchargé ; confirmez avec la commande lsmod.


<span style='color:red'>8.</span> Pour que le module soit chargé automatiquement au démarrage du système, il faut l’inscrire dans le
fichier /etc/modules. Essayez, et vérifiez avec la commande lsmod après redémarrage de la machine.


## Exercice 3.

<span style='color:red'>1.</span> Commencez par écrire un script qui recopie dans un fichier tmp.txt chaque ligne saisie au clavier par
l’utilisateur


<span style='color:red'>2.</span> Lancez votre script et appuyez sur CTRL+Z. Que se passe-t-il ? Comment faire pour que le script pour-
suive son exécution ?


<span style='color:red'>3.</span> Toujours pendant l’exécution du script, appuyez sur CTRL+C. Que se passe-t-il ?


<span style='color:red'>4.</span> Modifiez votre script pour redéfinir les actions à effectuer quand le script reçoit les signaux SIGTSTP (= CTRL+Z) et SIGINT (= CTRL+C) : dans le premier cas, il doit afficher ”Impossible de me placer en
arrière-plan”, et dans le second cas, il doit afficher ”OK, je fais un peu de ménage avant” avant de
supprimer le fichier temporaire et terminer le script.


<span style='color:red'>5.</span> Testez le nouveau comportement de votre script en utilisant d’une part les raccourcis clavier, d’autre
part la commande kill


<span style='color:red'>6.</span> Relancez votre script et faites immédiatement un CTRL+C : vous obtenez un message d’erreur vous
indiquant que le fichier tmp.txt n’existe pas. A l’aide de la commande interne test, corrigez votre script pour que ce message n’apparaisse plus.


## Exercice 4. Surveillance de l’activité du système

<span style='color:red'>1.</span> Dans tty1, lancez la commande htop, puis tapez la commande w dans tty2. Qu’affiche cette com-
mande ?


<span style='color:red'>2.</span> Comment afficher l’historique des dernières connexions à la machine ?


<span style='color:red'>3.</span> Quelle commande permet d’obtenir la version du noyau ?


<span style='color:red'>4.</span> Comment récupérer toutes les informations sur le processeur, au format JSON ?


<span style='color:red'>5.</span> Comment obtenir la liste des derniers démarrages de la machine avec la commande journalctl ?
Comment afficher tout ce qu’il s’est passé sur la machine lors de l’avant-dernier boot ?


<span style='color:red'>6.</span> Comment obtenir la liste des derniers démarrages de la machine avec la commande journalctl ?


<span style='color:red'>7.</span> Faites en sortes que lors d’une connexion à la machine, les utilisateurs soient prévenus par un message à l’écran d’une maintenance le 26 mars à minuit. Editer le fichier /etc/motd


<span style='color:red'>8.</span> Ecrivez un script bash qui permet de calculer le k-ième nombre de Fibonacci : Fk = Fk−1 + Fk−2,
avec F0 = F1 = 1. Lancez le calcul de F100 puis lancez la commande tload depuis un autre terminal
virtuel. Que constatez-vous ? Interrompez ensuite le calcul avec CTRL+C et observez la conséquence sur
l’affichage de tload.
