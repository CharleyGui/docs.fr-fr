---
title: Types de collection F#
description: En savoir plus sur F# quoi ils diffèrent des types de collections dans le .NET Framework et les types de collections.
ms.date: 05/16/2016
ms.openlocfilehash: b370d850deaacc961dff9515ffa8c20634af4ed6
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041724"
---
# <a name="f-collection-types"></a>Types de collection F#

En passant en revue cette rubrique, vous pouvez déterminer le F# type de collection meilleures adapté à un besoin particulier. Ces types de collections diffèrent des types de collection dans le .NET Framework, telles que celles de la `System.Collections.Generic` espace de noms, qui les F# les types de collection sont conçus de contexte de la programmation fonctionnelle au lieu d’orienté objet point de vue. Plus précisément, seul le regroupement de tableau comporte des éléments mutables. Par conséquent, lorsque vous modifiez une collection, vous créez une instance de la collection modifiée au lieu de la modification de la collection d’origine.

Types de collections diffèrent également dans le type de structure de données dans lequel les objets sont stockés. Structures de données telles que les tables de hachage, les listes liées et les tableaux ont des caractéristiques de performances différentes et un ensemble différent d’opérations disponibles.

## <a name="f-collection-types"></a>Types de collection F#

Le tableau suivant présente F# types de collections.

|Type|Description|Liens associés|
|----|-----------|-------------|
|[List](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Obtenir la série immuable et ordonnée d’éléments du même type. Implémenté comme une liste liée.|[Listes](lists.md)<br /><br />[Module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[tableau](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Une collection de taille fixe, de base zéro et mutable d’éléments de données consécutifs qui sont tous du même type.|[Tableaux](arrays.md)<br /><br />[Module Array](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2D Module](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Module de Array3D](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[seq](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Une série logique d’éléments qui sont tous d’un type. Les séquences sont particulièrement utiles lorsque vous avez une vaste collection ordonnée de données, mais ne pensez pas nécessairement utiliser tous les éléments. Séquence des éléments sont calculées uniquement en tant que cela est nécessaire une séquence peut être plus performant qu’une liste si ce n’est pas tous les éléments sont utilisés. Les séquences sont représentées par le `seq<'T>` type, qui est un alias pour `IEnumerable<T>`. Par conséquent, n’importe quel type .NET Framework qui implémente `System.Collections.Generic.IEnumerable<'T>` peut être utilisé comme une séquence.|[Séquences](sequences.md)<br /><br />[Module Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Carte](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Dictionnaire immuable d’éléments. Éléments accessibles par clé.|[Module de mappage](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Set](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Un ensemble immuable qui est basé sur les arborescences binaires, où la comparaison est la F# fonction de comparaison structurelle, qui utilise potentiellement des implémentations de la `System.IComparable` interface sur les valeurs de clé.|[Module de jeu](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Table de fonctions

Cette section compare les fonctions qui sont disponibles sur F# types de collections. La complexité des calculs de la fonction est donnée, où N est la taille de la première collection, et où M est la taille de la deuxième collection, le cas échéant. Un tiret (-) indique que cette fonction n’est pas disponible sur la collection. Étant donné que les séquences sont évaluées en différé, une fonction telle que Seq.distinct peut être o (1), car elle retourne immédiatement, bien qu’il affecte toujours les performances de la séquence lors de l’énumération.

|Fonction|Tableau|Liste|Séquence|Carte|Définir|Description|
|--------|-----|----|--------|---|---|-----------|
|append|O(M)|O(N)|O(N)|-|-|Retourne une nouvelle collection qui contient les éléments de la première collection de suivis des éléments de la seconde collection.|
|add|-|-|-|O (log N)|O (log N)|Retourne une nouvelle collection avec l’élément ajouté.|
|Moyenne|O(N)|O(N)|O(N)|-|-|Retourne la moyenne des éléments dans la collection.|
|averageBy|O(N)|O(N)|O(N)|-|-|Retourne la moyenne des résultats de la fonction fournie appliquée à chaque élément.|
|blit|O(N)|-|-|-|-|Copie une section d’un tableau.|
|cache|-|-|O(N)|-|-|Calcule et stocke des éléments d’une séquence.|
|cast|-|-|O(N)|-|-|Convertit les éléments vers le type spécifié.|
|Choisissez|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée `f` à chaque élément `x` de la liste. Retourne la liste qui contient les résultats pour chaque élément où la fonction retourne `Some(f(x))`.|
|collecter|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à chaque élément de la collection, concatène tous les résultats et retourne la liste combinée.|
|compareWith|-|-|O(N)|-|-|Compare deux séquences à l’aide de la fonction de comparaison donnée, élément par élément.|
|concat|O(N)|O(N)|O(N)|-|-|Combine l’énumération d’énumérations données en une énumération concaténée unique.|
|contains|-|-|-|-|O (log N)|Retourne la valeur true si l’ensemble contient l’élément spécifié.|
|containsKey|-|-|-|O (log N)|-|Teste si un élément est dans le domaine d’un mappage.|
|count|-|-|-|-|O(N)|Retourne le nombre d'éléments figurant dans le jeu.|
|countBy|-|-|O(N)|-|-|Applique une fonction génératrice de clé à chaque élément d’une séquence et retourne une séquence qui produit des clés uniques et leur nombre d’occurrences dans la séquence d’origine.|
|copy|O(N)|-|O(N)|-|-|Copie la collection.|
|create|O(N)|-|-|-|-|Crée un tableau d’éléments entiers qui sont tous initialement la valeur donnée.|
|Délai|-|-|O(1)|-|-|Retourne une séquence qui est générée à partir de la spécification différée donnée d’une séquence.|
|différence|-|-|-|-|O (M &#42; log N)|Retourne un nouveau jeu avec les éléments du second ensemble supprimés du premier jeu.|
|distinct|||O(1)&#42;|||Retourne une séquence qui ne contient aucune entrée en double conformément aux comparaisons de hachage et d’égalité génériques sur les entrées. Si un élément apparaît plusieurs fois dans la séquence, les occurrences ultérieures sont ignorées.|
|distinctBy|||O(1)&#42;|||Retourne une séquence qui ne contient aucune entrée en double selon les comparaisons de hachage et d’égalité génériques sur les clés qui retourne la fonction génératrice de clé donnée. Si un élément apparaît plusieurs fois dans la séquence, les occurrences ultérieures sont ignorées.|
|vide|O(1)|O(1)|O(1)|O(1)|O(1)|Crée une collection vide.|
|exists|O(N)|O(N)|O(N)|O (log N)|O (log N)|Teste si un élément de la séquence répond au prédicat donné.|
|exists2|O(min(N,M))|-|O(min(N,M))|||Teste si une paire d’éléments correspondants des séquences d’entrée répond au prédicat donné.|
|fill|O(N)|||||Définit une plage d’éléments du tableau à la valeur donnée.|
|filtre|O(N)|O(N)|O(N)|O(N)|O(N)|Retourne une nouvelle collection qui contienne uniquement les éléments de la collection pour lesquels le prédicat donné retourne `true`.|
|find|O(N)|O(N)|O(N)|O (log N)|-|Retourne le premier élément pour lequel la fonction donnée retourne `true`. Retourne `System.Collections.Generic.KeyNotFoundException` si cet élément n’existe.|
|findIndex|O(N)|O(N)|O(N)|-|-|Retourne l’index du premier élément du tableau qui répond au prédicat donné. Déclenche `System.Collections.Generic.KeyNotFoundException` si aucun élément ne satisfait le prédicat.|
|findKey|-|-|-|O (log N)|-|Évalue la fonction sur chaque mappage dans la collection et retourne la clé pour le premier mappage où la fonction retourne `true`. Si cet élément n’existe, cette fonction lève `System.Collections.Generic.KeyNotFoundException`.|
|pli|O(N)|O(N)|O(N)|O(N)|O(N)|Applique une fonction à chaque élément de la collection, un argument d’accumulation à travers le calcul de thread. Si la fonction d’entrée est f et les éléments sont i0... iN, cette fonction calcule f (...) (f s i0)...) Dans.|
|fold2|O(N)|O(N)|-|-|-|Applique une fonction aux éléments correspondants de deux collections, un argument d’accumulation à travers le calcul de thread. Les collections doivent avoir des tailles identiques. Si la fonction d’entrée est f et les éléments sont i0... iN et j0... jN, cette fonction calcule f (...) (s f i0 j0)...) Dans jN.|
|foldBack|O(N)|O(N)|-|O(N)|O(N)|Applique une fonction à chaque élément de la collection, un argument d’accumulation à travers le calcul de thread. Si la fonction d’entrée est f et les éléments sont i0... iN, cette fonction calcule f i0 (...) (f en s)).|
|foldBack2|O(N)|O(N)|-|-|-|Applique une fonction aux éléments correspondants de deux collections, un argument d’accumulation à travers le calcul de thread. Les collections doivent avoir des tailles identiques. Si la fonction d’entrée est f et les éléments sont i0... iN et j0... jN, cette fonction calcule f i0 j0 (...) (f dans jN s)).|
|ForAll|O(N)|O(N)|O(N)|O(N)|O(N)|Teste si tous les éléments de la collection répondent au prédicat donné.|
|forall2|O(N)|O(N)|O(N)|-|-|Teste si tous les éléments correspondants de la collection répondent au prédicat donné par paire.|
|obtenir / nième|O(1)|O(N)|O(N)|-|-|Retourne un élément à partir de la fonction de son index de collection.|
|head|-|O(1)|O(1)|-|-|Retourne le premier élément de la collection.|
|init|O(N)|O(N)|O(1)|-|-|Crée une collection à partir de la dimension et une fonction de générateur pour calculer les éléments.|
|initInfinite|-|-|O(1)|-|-|Génère une séquence qui, lorsqu’elle est itérée, retourne des éléments consécutifs en appelant la fonction donnée.|
|intersect|-|-|-|-|O (log N &#42; journal M)|Calcule l’intersection de deux jeux.|
|intersectMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Calcule l’intersection d’une séquence de jeux. La séquence ne doit pas être vide.|
|isEmpty|O(1)|O(1)|O(1)|O(1)|-|Retourne `true` si la collection est vide.|
|isProperSubset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du premier jeu figurent dans le deuxième jeu, et au moins un élément du second jeu n’est pas dans le premier jeu.|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du second jeu figurent dans le premier jeu, et au moins un élément du premier jeu n’est pas dans le deuxième jeu.|
|isSubset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du premier jeu figurent dans le deuxième jeu.|
|isSuperset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du second jeu figurent dans le premier jeu.|
|Iter|O(N)|O(N)|O(N)|O(N)|O(N)|Applique la fonction donnée à chaque élément de la collection.|
|iteri|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à chaque élément de la collection. L’entier qui est passé à la fonction indique l’index de l’élément.|
|iteri2|O(N)|O(N)|-|-|-|Applique la fonction donnée à une paire d’éléments qui sont obtenue en faisant correspondre les index de deux tableaux. L’entier qui est passé à la fonction indique l’index des éléments. Les deux tableaux doivent avoir la même longueur.|
|iter2|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à une paire d’éléments qui sont obtenue en faisant correspondre les index de deux tableaux. Les deux tableaux doivent avoir la même longueur.|
|last|O(1)|O(N)|O(N)|-|-|Retourne le dernier élément dans la collection applicable.|
|length|O(1)|O(N)|O(N)|-|-|Retourne le nombre d’éléments dans la collection.|
|map|O(N)|O(N)|O(1)|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée à chaque élément du tableau.|
|map2|O(N)|O(N)|O(1)|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des deux collections par paire. Les deux tableaux d’entrée doivent avoir la même longueur.|
|map3|-|O(N)|-|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des trois collections simultanément.|
|mapi|O(N)|O(N)|O(N)|-|-|Génère un tableau dont les éléments sont les résultats de l’application de la fonction donnée à chaque élément du tableau. L’index d’entiers passé à la fonction indique l’index de l’élément qui est en cours de transformation.|
|mapi2|O(N)|O(N)|-|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des deux collections, en passant également l’index des éléments. Les deux tableaux d’entrée doivent avoir la même longueur.|
|max|O(N)|O(N)|O(N)|-|-|Retourne le plus grand élément dans la collection, par rapport à l’aide de la [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) opérateur.|
|maxBy|O(N)|O(N)|O(N)|-|-|Retourne le plus grand élément dans la collection, par rapport à l’aide de [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) le résultat de la fonction.|
|maxElement|-|-|-|-|O (log N)|Retourne l’élément plus grand dans le jeu selon l’ordre qui est utilisé pour le jeu.|
|min|O(N)|O(N)|O(N)|-|-|Retourne l’élément minimum dans la collection, par rapport à l’aide de la [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) opérateur.|
|minBy|O(N)|O(N)|O(N)|-|-|Retourne l’élément minimum dans la collection, par rapport à l’aide de la [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) opérateur sur le résultat de fonction.|
|minElement|-|-|-|-|O (log N)|Retourne l’élément le plus bas dans le jeu selon l’ordre qui est utilisé pour le jeu.|
|ofArray|-|O(N)|O(1)|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que le tableau donné.|
|ofList|O(N)|-|O(1)|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que la liste donnée.|
|ofSeq|O(N)|O(N)|-|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que la séquence donnée.|
|par paire|-|-|O(N)|-|-|Retourne une séquence de chaque élément dans la séquence d’entrée et son prédécesseur, à l’exception du premier élément, qui est retourné uniquement comme prédécesseur du deuxième élément.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Fractionne la collection en deux collections. La première collection contient les éléments pour lesquels le prédicat donné retourne `true`, et la deuxième collection contient les éléments pour lesquels le prédicat donné retourne `false`.|
|Permute)|O(N)|O(N)|-|-|-|Retourne un tableau avec tous les éléments permutés en fonction de la permutation spécifiée.|
|choix|O(N)|O(N)|O(N)|O (log N)|-|Applique la fonction donnée à des éléments consécutifs, en retournant le premier résultat où la fonction retourne Some. Si la fonction ne retourne jamais certains, `System.Collections.Generic.KeyNotFoundException` est déclenché.|
|readonly|-|-|O(N)|-|-|Crée un objet de séquence qui délègue à l’objet de séquence donné. Cette opération garantit un cast de type ne peut pas redécouvrir et muter la séquence d’origine. Par exemple, si un tableau, la séquence retournée retournera les éléments du tableau, mais vous ne pouvez pas effectuer un cast de l’objet de séquence retourné en un tableau.|
|reduce|O(N)|O(N)|O(N)|-|-|Applique une fonction à chaque élément de la collection, un argument d’accumulation à travers le calcul de thread. Cette fonction démarre en appliquant la fonction aux deux premiers éléments, il transmet ce résultat dans la fonction avec le troisième élément et ainsi de suite. La fonction retourne le résultat final.|
|reduceBack|O(N)|O(N)|-|-|-|Applique une fonction à chaque élément de la collection, un argument d’accumulation à travers le calcul de thread. Si la fonction d’entrée est f et les éléments sont i0... iN, cette fonction calcule f i0 (...) (f dans-1 iN)).|
|remove|-|-|-|O (log N)|O (log N)|Supprime un élément du domaine de la carte. Aucune exception n’est levée si l’élément n’est pas présent.|
|répliquer|-|O(N)|-|-|-|Crée une liste d’une longueur spécifiée avec tous les éléments la valeur donnée.|
|Rév.|O(N)|O(N)|-|-|-|Retourne une nouvelle liste avec les éléments dans l’ordre inverse.|
|analyse|O(N)|O(N)|O(N)|-|-|Applique une fonction à chaque élément de la collection, un argument d’accumulation à travers le calcul de thread. Cette opération s’applique à la fonction pour le deuxième argument et le premier élément de la liste. L’opération puis passe ce résultat dans la fonction avec le deuxième élément et ainsi de suite. Enfin, l’opération retourne la liste des résultats intermédiaires et le résultat final.|
|scanBack|O(N)|O(N)|-|-|-|Ressemble à l’opération foldBack mais retourne les résultats intermédiaires et finaux.|
|singleton|-|-|O(1)|-|O(1)|Retourne une séquence qui produit un seul élément.|
|définir|O(1)|-|-|-|-|Définit un élément d’un tableau à la valeur spécifiée.|
|skip|-|-|O(N)|-|-|Retourne une séquence qui ignore N éléments de la séquence sous-jacente, puis produit les éléments restants de la séquence.|
|skipWhile|-|-|O(N)|-|-|Retourne une séquence qui, lorsqu’elle est itérée, ignore les éléments de la séquence sous-jacente lorsque le prédicat donné retourne `true` , puis produit les éléments restants de la séquence.|
|sort|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|O (N log N)|O (N log N)|-|-|Trie la collection par valeur de l’élément. Les éléments sont comparés à l’aide de [comparer](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|O (N log N)|O (N log N)|-|-|Trie la liste donnée à l’aide de clés qui fournit la projection donnée. Les clés sont comparées à l’aide de [comparer](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|-|-|-|-|Trie les éléments d’un tableau en faisant muter sur place et à l’aide de la fonction de comparaison donnée. Les éléments sont comparés à l’aide de [comparer](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|-|-|-|-|Trie les éléments d’un tableau en faisant muter sur place et à l’aide de la projection donnée pour les clés. Les éléments sont comparés à l’aide de [comparer](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|-|-|-|-|Trie les éléments d’un tableau en faisant muter sur place et à l’aide de la fonction de comparaison donnée en tant que l’ordre.|
|sortWith|Moyenne de O (N log N)<br /><br />O(N^2) pire des cas|O (N log N)|-|-|-|Trie les éléments d’une collection, à l’aide de la fonction de comparaison donnée en tant que l’ordre et en retournant une nouvelle collection.|
|sub|O(N)|-|-|-|-|Génère un tableau qui contient la sous-plage donnée spécifiée par l’index de départ et longueur.|
|sum|O(N)|O(N)|O(N)|-|-|Retourne la somme des éléments dans la collection.|
|sumBy|O(N)|O(N)|O(N)|-|-|Retourne la somme des résultats générés en appliquant la fonction à chaque élément de la collection.|
|fin du|-|O(1)|-|-|-|Retourne la liste sans son premier élément.|
|Take|-|-|O(N)|-|-|Retourne les éléments de la séquence jusqu'à un nombre spécifié.|
|takeWhile|-|-|O(1)|-|-|Retourne une séquence qui, lorsqu’elle est itérée, produit les éléments de la séquence sous-jacente lorsque le prédicat donné retourne `true` , puis ne retourne aucun autre élément.|
|toArray|-|O(N)|O(N)|O(N)|O(N)|Crée un tableau à partir de la collection donnée.|
|ToList|O(N)|-|O(N)|O(N)|O(N)|Crée une liste à partir de la collection donnée.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Crée une séquence à partir de la collection donnée.|
|truncate|-|-|O(1)|-|-|Retourne une séquence qui, lorsqu’elle est énumérée, retourne pas plus de N éléments.|
|tryFind|O(N)|O(N)|O(N)|O (log N)|-|Recherche un élément qui satisfait à un prédicat donné.|
|tryFindIndex|O(N)|O(N)|O(N)|-|-|Recherche le premier élément qui répond un prédicat spécifié et retourne l’index de l’élément correspondant, ou `None` si cet élément n’existe.|
|tryFindKey|-|-|-|O (log N)|-|Retourne la clé du premier mappage dans la collection qui répond au prédicat donné, ou retourne `None` si cet élément n’existe.|
|tryPick|O(N)|O(N)|O(N)|O (log N)|-|Applique la fonction donnée à des éléments consécutifs, en retournant le premier résultat où la fonction retourne `Some` pour une valeur. Si cet élément n’existe, l’opération retourne `None`.|
|unfold|-|-|O(N)|-|-|Retourne une séquence qui contient les éléments qui génère le calcul donné.|
|union|-|-|-|-|O (M &#42; log N)|Calcule l’union des deux jeux.|
|unionMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Calcule l’union d’une séquence de jeux.|
|unzip|O(N)|O(N)|O(N)|-|-|Fractionne une liste de paires en deux listes.|
|unzip3|O(N)|O(N)|O(N)|-|-|Fractionne une liste de triples en trois listes.|
|fenêtrées|-|-|O(N)|-|-|Retourne une séquence qui produit des fenêtres défilantes de contenant les éléments sont tirés de la séquence d’entrée. Chaque fenêtre est retournée en tant que nouveau tableau.|
|zip|O(N)|O(N)|O(N)|-|-|Combine les deux collections dans une liste de paires. Les deux listes doivent avoir des longueurs égales.|
|zip3|O(N)|O(N)|O(N)|-|-|Combine les trois collections dans une liste de triples. Les listes doivent avoir des longueurs égales.|

## <a name="see-also"></a>Voir aussi

- [Types F#](fsharp-types.md)
- [Informations de référence du langage F#](index.md)
