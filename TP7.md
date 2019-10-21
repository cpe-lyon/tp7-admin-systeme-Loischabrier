Loïs CHABRIER

# _TP 3 - Gestion des paquets_

## Exercice 1. Commandes de base

<br>
<span style='color:red'></span> Commencez par mettre à jour votre système avec les commandes vues dans le cours.
</span>

`sudo apt upgrade` puis `sudo apt update`

<span style='color:red'>1.</span> Quels sont les 5 derniers paquets installés sur votre machine ?

  - `snapd.list`
  - `sosreport.list`
  - `ubuntu-server.list`
  - `unattended-upgrades.list`
  - `cloud-init.list`

<span style='color:red'>2.</span> Utiliser dpkg et apt pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage ?

Pour 'dpkg' : `dpkg --list | wc --lines` (524 ici)
Pour 'apt' : `apt list --installed | wc --lines` (520 ici)


<span style='color:red'>3.</span> Combien de paquets sont disponibles en téléchargement ?

Il faut faire : `apt list | wc -l`

<span style='color:red'>4.</span> Créer un alias “maj” qui met à jour le système.

Dans `~/.bashrc` : `alias maj="sudo apt update && sudo apt upgrade"`

<span style='color:red'>5.</span> A quoi sert le paquet fortunes ? Installez-le.

Il sert à afficher des proverbes ou des citations dans le terminal. Pour l'installer, il faut taper `sudo apt install fortune-mod`.

<span style='color:red'>6.</span> Quels paquets proposent de jouer au sudoku ?

Grâce à la commande `apt search sudoku`, on obtient tout les paquets qui proposent le sudoku.

      fltk1.1-games/disco 1.1.10-26ubuntu1 amd64
        Boîte à outils Fast Light - exemples de jeux : jeux de dames, sudoku

      fltk1.3-games/disco 1.3.4-9ubuntu1 amd64
        Boîte à outils Fast Light - exemples de jeux : jeux de dames, sudoku

      gnome-sudoku/disco 1:3.32.0-1 amd64
        Casse-tête Sudoku pour GNOME

      hitori/disco 3.31.0-1 amd64
        Jeu de puzzle logique similaire au sudoku

      ksudoku/disco 4:18.12.3-0ubuntu1 amd64
        Jeu et Solveur de Sudoku

      libqqwing-dev/disco 1.3.4-1.1 amd64
        outil pour générer et résoudre des casse-tête Sudoku (développement)

      libqqwing2v5/disco 1.3.4-1.1 amd64
        outil pour générer et résoudre des casse-tête Sudoku (bibliothèque)

      nudoku/disco 1.0.0-1 amd64
        ncurses based sudoku games

      qqwing/disco 1.3.4-1.1 amd64
        tool for generating and solving Sudoku puzzles (application)

      sudoku/disco 1.0.5-2build3 amd64
        Sudoku en mode console

      texlive-games/disco 2018.20190227-1 all
        TeX Live : Composition de jeux


<span style='color:red'>7.</span> Lister les derniers paquets installés explicitement avec la commande `apt install`

`grep "apt install" /var/log/apt/history.log`

## Exercice 2.

A partir de quel paquet est installée la commande ls ? Comment obtenir cette information en une seule
commande, pour n’importe quel programme (indice : la réponse est dans le poly de cours 2, dans la liste des
commandes utiles) ? Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension .sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.

`which -a ls | xargs dpkg -s 2>/dev/null`

        if [ -z "$1" ]; then
              echo "Veuillez fournir un nom de commande"
        else
              dpkg -S $(which "$1");
        fi

## Exercice 3.

Ecrire une commande qui affiche “INSTALLÉ” ou “NON INSTALLÉ” selon le nom et le statut du package
spécifié dans cette commande.

`(dpkg -l "nom_package" | grep "^ii") && echo "installé" || echo "non installé"`

## Exercice 4.

Lister les programmes livrés avec coreutils. A quoi sert la commande ’[’ et comment afficher ce qu’elle
retourne ?

`apt show coreutils` pour lister les programmes.
`[` est l'équivalent de `test`.

## Exercice 5.

Installez le paquet emacs à l’aide de la version graphique d’aptitude.

Taper `aptitude` 
Ensuite taper `/` pour chercher le paquet emacs 
Sélectionner le paquets emacs 
Puis + ig <entré> g et le paquet s'installe. 

## Exercice 6.

Installer la version Oracle de Java (avec l’ajout des PPA)

    sudo add-apt-repository ppa:linuxuprising/java
    sudo apt update
    sudo apt install oracle-java12-installer

Vérifiez qu’un nouveau fichier a été créé dans /etc/apt/sources.list.d. Que contient-il ?

    cd /etc/apt/source.list.d
    ls
    linuxuprising-ubuntu-java-disco.list
