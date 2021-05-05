Objectifs du TP
Manipulation de données avec HBase, et traitement co-localisé avec Spark.

Outils et Versions¶
Apache HBase Version 1.4.7
Apache Hadoop Version: 2.7.2
Apache Spark Version: 2.2.1
Docker Version 17.09.1
IntelliJ IDEA Version Ultimate 2016.1 (ou tout autre IDE de votre choix)
Java Version 1.8
Unix-like ou Unix-based Systems (Divers Linux et MacOS)
Apache HBase¶
Présentation¶
HBase est un système de gestion de bases de données distribué, non-relationnel et orienté colonnes, développé au-dessus du système de fichier HDFS.
Il permet un accès aléatoire en écriture/lecture en temps réel à un très grand ensemble de données.

Modèle de données¶
Le modèle se base sur six concepts, qui sont :

Table : dans HBase les données sont organisées dans des tables. Les noms des tables sont des chaînes de caractères.
Row : dans chaque table, les données sont organisées dans des lignes. Une ligne est identifiée par une clé unique (RowKey). La Rowkey n’a pas de type, elle est traitée comme un tableau d’octets.
Column Family : Les données au sein d’une ligne sont regroupées par column family. Chaque ligne de la table a les mêmes column families, qui peuvent être peuplées ou pas. Les column families sont définies à la création de la table dans HBase. Les noms des column families sont des chaînes de caractères.
Column qualifier : L’accès aux données au sein d’une column family se fait via le column qualifier ou column. Ce dernier n’est pas spécifié à la création de la table mais plutôt à l’insertion de la donnée. Comme les rowkeys, le column qualifier n’est pas typé, il est traité comme un tableau d’octets.
Cell : La combinaison du RowKey, de la Column Family ainsi que la Column qualifier identifie d’une manière unique une cellule. Les données stockées dans une cellule sont appelées les valeurs de cette cellule. Les valeurs n’ont pas de type, ils sont toujours considérés comme tableaux d’octets.
Version : Les valeurs au sein d’une cellule sont versionnés. Les versions sont identifiés par leur timestamp (de type long). Le nombre de versions est configuré via la Column Family. Par défaut, ce nombre est égal à trois.
