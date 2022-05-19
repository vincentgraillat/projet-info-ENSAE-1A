# WordCloud
Projet dans le cadre du cours d'introduction à Python (1A ENSAE)

### 1.1. Présentation du projet

L’objectif est d’observer l’évolution de la crise du coronavirus à travers **l’analyse des discours du président E. Macron**. Pour que cette analyse soit vraiment la plus précise et la moins biaisée possible, nous avons choisis de sélectionner uniquement les discours sous la forme d'adresse aux Français et qui sont recensés sur le site de l'Elysée. Ces discours ont l'avantage d'avoir le même public visé, la même forme et même le même lieu. Nous avons donc un corpus de 9 discours entre le 12 Mars 2020 et le 9 Novembre 2021. Ces textes devraient donc être particulièrement pertinent pour observer l'évolution de la crise. 

Pour mener notre analyse il nous faudra extraire les mots clés de ces discours (text clouds). Pour cela, nous allons coder en Python un WordCloud qui permet **d'afficher de façon graphique les mots clés de chaque discours**. 

Avec un WordCloud pour les différents discours d'Emmanuel Macron depuis le début de la crise, nous serons capable de voir **l'évolution de sa stratégie de communication**.

### 1.2. Méthodologie

Il y a plusieurs méthodes pour coder un WordCloud i.e. un algorithme qui extrait les mots clés d’un texte et les représente selon leur importance.

Au cours de nos travaux nous avons pu tester deux méthodes différentes : **une méthode assez expérimentale**, où nous avons testé plusieurs sous-méthodes pour améliorer notre rendu, et une méthode connue, **la méthode TF-IDF**, que nous avons utilisé pour faire nos analyses. 

Pour notre première méthode nous avons commencé par créer une fonction qui prend en appel un discours et retourne **le dictionnaire qui contient les mots du texte en clés et leur fréquence en valeur**. A partir de ce dictionnaire nous avons pu implémenter la fonction wordcloud qui prend en appel un nom de discours et la fonction créatrice de dictionnaire et renvoie le WordCloud obtenu à partir des fréquences du dictionnaire. Cette méthode naïve a pour inconvénient d’accorder **une importance démesurée aux petits mots** (« de », « et », etc), qui sont omniprésent sur le WordCloud. Son autre défaut est de ne pas faire **la différence entre des mots différents désignant pourtant la même chose**. Par exemple, cette méthode ne fera pas la différence entre "français" et "française". Ces deux mots seront comptés comme différents car ils ont des accords différents. 

Pour pallier à ces deux problèmes nous avons ajouter à cette méthode de ranking simple **des méthodes de nettoyage et de racinisation**. Pour le nettoyage nous avons simplement implémenter **une liste de "stopwords"** (les mots les plus communs de la langue française mais qui n'apportent rien aux propos). Pour la racinisation nous avons importer des bibliothèques Python censées faire ce travail pour nous. Cependant notre fonction de racinisation s'est avérée être loin de ce que nous attendions et nous avons donc décidé  de mettre de côté la phase de racinisation pour plus tard afin de nous concentrer d'abord sur le nettoyage dans un troisième temps.

Nous avons donc améliorer notre fonction de nettoyage en rajoutant de nous mêmes certains "stopwords", et en important une nouvelle bibliothèque (SpaCy) qui nous permet de mieux manipuler les mots de la langue française. 

Dans un quatrième temps nous avons importer une nouvelle bibliothèque, plus efficace, pour raciniser notre texte. Le rendu que nous avons obtenu est déjà beaucoup plus satisfaisant que précédemment mais certains problèmes persistent et la racinisation n'est pas parfaite. De même nous nous rendons compte que le nettoyage n'est toujours pas réellement pertinent, dans la mesure où, s'il y a bien des mots qui sont des "stopwords" peu importe le texte (comme, par exemple, les déterminants), **d'autres ne le seront que dans certains contextes**. 

Pour affiner notre WordCloud, nous avons donc utilisé **la méthode TF-IDF** qui permet de pondérer la fréquence des mots dans le texte par une moyenne représentative de leur usage dans la langue française à partir d'un corpus de texte assez large. Nous avons donc mis en place cette fonction, tout en réutilisant les fonctions créées dans la première méthode, et nous avons obtenues des WordCloud exploitables et analysables. 

### 1.3. Résultats obtenus et analyses

Nous vous présentons ici trois WordCloud que nous avons obtenues ainsi que l'analyse qui en découle: 

WordCloud du 16 Mars 2020: 

![WordCloud16mars](https://user-images.githubusercontent.com/95186190/169292557-5c5c320f-719d-43bc-8ba2-32c7c1748d99.png)

WordCloud du 14 Juin 2020:

![WordCloud14juin](https://user-images.githubusercontent.com/95186190/169292614-0a4a0117-3048-4d51-9c99-d03093971648.png)

WordCloud du 9 Novembre 2021:

![WordCloud9novembre](https://user-images.githubusercontent.com/95186190/169292650-13017977-8b0a-4a13-9fde-4ea2a58e02cf.png)

Dans son discours du 16 mars, le Président E. Macron change de rhétorique, avec un discours plus impératif. Le 16 mars, il annonce, en effet, le premier confinement (sans utiliser le mot). Cela s'observe dans le WordCloud avec l'utilisation des mots "décidé", qui montre un choix fait par le gouvernement, "dès" et "demain" (le confinement était effectif le lendemain), "nécessaire" montrant que c'est la seule issue possible et également que les commerces nécessaires resteront ouverts, "devons" qui montre le ton qui a changé. C'est bien d'un combat qu'il s'agit et E. Macron l'a bien compris et il accentue la gravité de ces propos, comme on peut le voir avec l'utilisation du mot "guerre" (avec sa fameuse répétition de la phrase "nous sommes en guerre"), qui ressort beaucoup dans ce deuxième discours.


Cela se ressent encore plus dans le discours du 14 juin 2020 : la priorité est alors la relance de l'économie (il n'y a qu'à voir la taille du vocable économie et de demain dans le WordCloud, quitte à relancer l'épidémie de la Covid. Le problème n'est plus que sanitaire mais aussi social : il faut donner espoir à une population lassée, les mots "reconstruction" et "emploi" montrent que le président veut créer un après-Covid différent, plus "solidaire", et tirer les leçons de la crise. Le président semble être plein d'espoirs quant à la suite des évènements. L'objectif est le retour à une vie normale : on peut le voir avec la présence de "retrouver", "revenir", et de "pleinement" dans le Wordcloud.


Enfin, en novembre 2021, E. Macron tire un bilan de la pandémie de Covid 19 et des efforts qui ont été réalisés depuis juillet., d'où l'apparition démesurée du mot "depuis", et du mot "vaccin" dans le wordcloud. Il met l'accent sur les victimes psychosociales du Covid, ceux qui ont éprouvé directement les conséquences de la crise. La rhétorique n'est plus alarmiste ni directive mais plutôt descriptive, il revient sur ce qui s'est bien passé dans la gestion de la vaccination. On peut voir que l'après Covid est là : la priorité est au travail, à la relance de la France et à la relance d'une société fragilisée par deux ans de crise.



### 1.4. Ouverture

Avec plus de temps, nous aurions aimé :
- améliorer le nettoyage de façon à pouvoir utiliser notre fonction cleaner_text_4 (qui dans l'idéal devait être plus pertinente que la cleaner_text_3) dans la méthode TF-IDF;
- optimiser nos algorithmes de façon à pouvoir élargir le corpus, sans que le coût algorithmique ne soit trop lourd, de façon à rendre la deuxième méthode TF-IDF encore plus pertinente ;
- soigner la représentation : le principal problème graphique des WordCloud est le choix des couleurs que nous ne maitrisons pas et qui peut invisibiliser certains mots (notamment la couleur violette qui est peu visible). Le langage HTML aurait pu être une façon d'améliorer le rendu visuel. On aurait aussi pu implémenter une couleur en fonction de la connotation négative / positive des mots (approche n-grammes, Sentiment Analysis).
