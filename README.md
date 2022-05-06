# wordcloud
Projet dans le cadre du cours d'introduction à Python (1A ENSAE)

### 1.1. Présentation du projet

L’objectif est d’**observer l’évolution de la crise du coronavirus** à travers l’**analyse des discours du Président Macron**. Il s’agira donc d’extraire les mots clés de ces discours (text clouds). Pour cela, il nous faudra **coder en Python un wordcloud**.

Avec un WordCloud pour les différents discours d'Emmanuel Macron depuis le début de la crise, nous serons capable de voir l'évolution de sa stratégie de communication.

### 1.2. Méthodologie

Il y a **plusieurs méthodes pour coder un wordcloud** i.e. un algorithme qui extrait les mots clés d’un texte et les représente.

La plus simple est de faire **un ranking des mots utilisés en fonction de leur fréquence d’apparition**. Cette méthode naïve de ne pas faire la différence entre des mots différents désignant pourtant la même chose. Par exemple, cette méthode ne fera pas la différence entre "français" et "française". Ces deux mots seront comptés comme différents car ils ont des accords différents. Pourtant, ils désignent la même idée : l'auteur du texte s'adresse aux Français. Pour qu'un WordCloud soit pertinent, il faudrait que, dans une telle situation, le programme prenne en compte que le mot "français" est apparu deux fois. Pour parvenir à cela, il nous faudra ajouter à la méthode de ranking simple **des méthodes de racinisation** (*stemming*).

En outre, le ranking simple présente aussi l’inconvénient d’accorder une importance démesurée aux petits mots (« de », « et », etc). On peut les supprimer en implémentant des ***stopwords***, mais le WordCloud ne sera toujours pas réellement pertinent, dans la mesure où, s'il y a bien des mots qui seront des stopwords peu importe le texte (comme, par exemple, les déterminants), d'autres ne le seront que dans certains contextes. Prenons par exemple deux textes consacrés à l'étude de l'origine de l'univers mais non forcément d'accord. Logiquement, le mot "univers" devrait être présent de nombreuses fois dans les deux textes, est-ce pour autant pertinent de lui attribuer un gros score et de le faire apparaître en gros dans chacun des deux WordCloud ? Pas vraiment. Il faut donc pondérer les fréquences d’apparition des mots en fonction d’une moyenne de leur apparition dans un corpus de textes représentatifs de l’usage usuel de ces mots. C’est **la méthode TF-IDF** que nous utiliserons pour affiner notre WordCloud. Avec un WordCloud pour les différents discours d'Emmanuel Macron depuis le début de la crise, nous serons capable de voir l'évolution de sa stratégie de communication.

**1.3. Ouverture**

Avec plus de temps, nous aurions aimé :
- améliorer le nettoyage en conservant les majuscules des noms propres et la forme d’origine de chaque catégories grammaticales différentes ;
- améliorer les performances : élargir le corpus pour rendre la deuxième méthode TF-IDF encore plus pertinente, tester d'autres méthodes (Okapi BM25) ;
- soigner la représentation : implémenter une couleur en fonction de la connotation négative / positive des mots (approche n-grammes, Sentiment Analysis) et méliorer le rendu visuel grâce au langage HTML.
