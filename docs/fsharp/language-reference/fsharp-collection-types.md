---
title: Types de collection
description: En savoir F# plus sur les types de collections et leurs différences par rapport aux types de collections du .NET Framework.
ms.date: 05/16/2016
ms.openlocfilehash: df34a18e7762c52e169aa8a69709ae16064c134d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628863"
---
# <a name="f-collection-types"></a>Types de collection F#

En examinant cette rubrique, vous pouvez déterminer F# le type de collection qui convient le mieux à un besoin particulier. Ces types de collections diffèrent des types de collections dans le .NET Framework, tels que ceux de l’espace de noms `System.Collections.Generic` F# , dans le sens où les types de collections sont conçus d’un point de vue de la programmation fonctionnelle plutôt que d’une perspective orientée objet. Plus précisément, seule la collection de tableaux a des éléments mutables. Par conséquent, lorsque vous modifiez une collection, vous créez une instance de la collection modifiée au lieu de modifier la collection d’origine.

Les types de collections diffèrent également dans le type de la structure de données dans laquelle les objets sont stockés. Les structures de données telles que les tables de hachage, les listes liées et les tableaux ont des caractéristiques de performances différentes et un ensemble différent d’opérations disponibles.

## <a name="f-collection-types"></a>Types de collection F#

Le tableau suivant présente F# les types de collections.

|Type|Description|Liens connexes|
|----|-----------|-------------|
|[Liste](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Série immuable et ordonnée d’éléments du même type. Implémenté en tant que liste liée.|[Listes](lists.md)<br /><br />[Module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Tableau](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Collection mutable de taille fixe, de base zéro d’éléments de données consécutifs qui sont tous du même type.|[Tableaux](arrays.md)<br /><br />[Module de tableau](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Module Array2D](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Module Array3D](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[séquentiel](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Série logique d’éléments qui sont tous d’un type. Les séquences sont particulièrement utiles lorsque vous disposez d’une collection de données volumineuse et ordonnée, mais que vous n’envisagez pas nécessairement d’utiliser tous les éléments. Les éléments de séquence individuels sont calculés uniquement en fonction des besoins, de sorte qu’une séquence peut être plus performante qu’une liste si tous les éléments ne sont pas utilisés. Les séquences sont représentées par le type de `seq<'T>`, qui est un alias pour `IEnumerable<T>`. Par conséquent, tout type de .NET Framework qui implémente `System.Collections.Generic.IEnumerable<'T>` peut être utilisé comme une séquence.|[Séquences](sequences.md)<br /><br />[Module Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Map](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Dictionnaire immuable d’éléments. Les éléments sont accessibles par clé.|[Module de mappage](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Définir](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Ensemble immuable basé sur des arborescences binaires, où la comparaison est la F# fonction de comparaison structurelle qui utilise potentiellement des implémentations de l’interface `System.IComparable` sur des valeurs de clés.|[Définir le module](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Table des fonctions

Cette section compare les fonctions qui sont disponibles sur F# les types de collection. La complexité de calcul de la fonction est donnée, où N est la taille de la première collection et M est la taille de la deuxième collection, le cas échéant. Un tiret (-) indique que cette fonction n’est pas disponible dans la collection. Étant donné que les séquences sont évaluées tardivement, une fonction telle que Seq. distinct peut être O (1), car elle est retournée immédiatement, bien qu’elle affecte toujours les performances de la séquence lors de l’énumération.

|Fonction|Array|List|Séquence|Mappage|Définissez|Description|
|--------|-----|----|--------|---|---|-----------|
|append|O(N)|O(N)|O(N)|-|-|Retourne une nouvelle collection qui contient les éléments de la première collection, suivis des éléments de la deuxième collection.|
|add|-|-|-|O (log N)|O (log N)|Retourne une nouvelle collection avec l’élément ajouté.|
|average|O(N)|O(N)|O(N)|-|-|Retourne la moyenne des éléments dans la collection.|
|averageBy|O(N)|O(N)|O(N)|-|-|Retourne la moyenne des résultats de la fonction fournie appliquée à chaque élément.|
|blit,|O(N)|-|-|-|-|Copie une section d’un tableau.|
|cache|-|-|O(N)|-|-|Calcule et stocke les éléments d’une séquence.|
|cast|-|-|O(N)|-|-|Convertit les éléments dans le type spécifié.|
|choose|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée `f` à chaque élément `x` de la liste. Retourne la liste qui contient les résultats pour chaque élément où la fonction retourne `Some(f(x))`.|
|collect|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à chaque élément de la collection, concatène tous les résultats et retourne la liste combinée.|
|compareWith|-|-|O(N)|-|-|Compare deux séquences à l’aide de la fonction de comparaison donnée, élément par élément.|
|concat|O(N)|O(N)|O(N)|-|-|Combine l’énumération d’énumérations donnée comme une énumération concaténée unique.|
|contains|-|-|-|-|O (log N)|Retourne la valeur true si l’ensemble contient l’élément spécifié.|
|containsKey|-|-|-|O (log N)|-|Teste si un élément est dans le domaine d’une classe Map.|
|count|-|-|-|-|O(N)|Retourne le nombre d'éléments figurant dans le jeu.|
|countBy (|-|-|O(N)|-|-|Applique une fonction génératrice de clé à chaque élément d’une séquence et retourne une séquence qui produit des clés uniques et leur nombre d’occurrences dans la séquence d’origine.|
|copy|O(N)|-|O(N)|-|-|Copie la collection.|
|create|O(N)|-|-|-|-|Crée un tableau d’éléments entiers qui sont tous initialement la valeur donnée.|
|delay|-|-|O(1)|-|-|Retourne une séquence qui est créée à partir de la spécification différée donnée d’une séquence.|
|différence|-|-|-|-|O (M &#42; log N)|Retourne un nouvel ensemble avec les éléments du deuxième jeu supprimé du premier jeu.|
|distinct|||O(1)&#42;|||Retourne une séquence qui ne contient aucune entrée en double conformément aux comparaisons de hachage et d’égalité génériques sur les entrées. Si un élément se trouve plusieurs fois dans la séquence, les occurrences ultérieures sont ignorées.|
|distinctBy|||O(1)&#42;|||Retourne une séquence qui ne contient aucune entrée en double conformément aux comparaisons de hachage et d’égalité génériques sur les clés retournées par la fonction de génération de clé donnée. Si un élément se trouve plusieurs fois dans la séquence, les occurrences ultérieures sont ignorées.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Crée une collection vide.|
|exists|O(N)|O(N)|O(N)|O (log N)|O (log N)|Teste si un élément de la séquence répond au prédicat donné.|
|exists2|O (min (N, M))|-|O (min (N, M))|||Teste si une paire d’éléments correspondants des séquences d’entrée répond au prédicat donné.|
|fill|O(N)|||||Définit une plage d’éléments du tableau à la valeur donnée.|
|Filter|O(N)|O(N)|O(N)|O(N)|O(N)|Retourne une nouvelle collection qui contient uniquement les éléments de la collection pour lesquels le prédicat donné retourne `true`.|
|trouver|O(N)|O(N)|O(N)|O (log N)|-|Retourne le premier élément pour lequel la fonction donnée retourne `true`. Retourne `System.Collections.Generic.KeyNotFoundException` si aucun élément de ce type n’existe.|
|findIndex|O(N)|O(N)|O(N)|-|-|Retourne l’index du premier élément du tableau qui répond au prédicat donné. Déclenche `System.Collections.Generic.KeyNotFoundException` si aucun élément ne répond au prédicat.|
|FindKey (|-|-|-|O (log N)|-|Évalue la fonction sur chaque mappage de la collection et retourne la clé pour le premier mappage où la fonction retourne `true`. Si aucun élément de ce type n’existe, cette fonction déclenche `System.Collections.Generic.KeyNotFoundException`.|
|Fold|O(N)|O(N)|O(N)|O(N)|O(N)|Applique une fonction à chaque élément de la collection, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Si la fonction d’entrée est f et que les éléments sont i0... Dans, cette fonction calcule f (... (f s I0)...) dans.|
|fold2|O(N)|O(N)|-|-|-|Applique une fonction aux éléments correspondants de deux collections, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Les collections doivent avoir des tailles identiques. Si la fonction d’entrée est f et que les éléments sont i0... Dans et j0... jN, cette fonction calcule f (... (f s I0 J0)...) Dans jN.|
|foldBack|O(N)|O(N)|-|O(N)|O(N)|Applique une fonction à chaque élément de la collection, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Si la fonction d’entrée est f et que les éléments sont i0... Dans, cette fonction calcule f i0 (... (f dans s).|
|foldBack2|O(N)|O(N)|-|-|-|Applique une fonction aux éléments correspondants de deux collections, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Les collections doivent avoir des tailles identiques. Si la fonction d’entrée est f et que les éléments sont i0... Dans et j0... jN, cette fonction calcule f i0 J0 (... (f dans jN s).|
|ForAll|O(N)|O(N)|O(N)|O(N)|O(N)|Teste si tous les éléments de la collection répondent au prédicat donné.|
|forall2|O(N)|O(N)|O(N)|-|-|Teste si tous les éléments correspondants de la collection satisfont à la paire de prédicat donnée.|
|Obtient/nth|O(1)|O(N)|O(N)|-|-|Retourne un élément de la collection en fonction de son index.|
|head|-|O(1)|O(1)|-|-|Retourne le premier élément de la collection.|
|init|O(N)|O(N)|O(1)|-|-|Crée une collection en fonction de la dimension et d’une fonction de générateur pour calculer les éléments.|
|initInfinite|-|-|O(1)|-|-|Génère une séquence qui, lorsqu’elle est itérée, retourne des éléments successifs en appelant la fonction donnée.|
|Coupe|-|-|-|-|O (log N &#42; journal M)|Calcule l’intersection de deux jeux.|
|intersectMany|-|-|-|-|O (N1 &#42; N2...)|Calcule l’intersection d’une séquence de jeux. La séquence ne doit pas être vide.|
|isEmpty|O(1)|O(1)|O(1)|O(1)|-|Retourne `true` si la collection est vide.|
|isProperSubset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du premier jeu figurent dans le deuxième jeu, et qu’au moins un élément du deuxième jeu n’est pas dans le premier jeu.|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du second jeu figurent dans le premier jeu, et qu’au moins un élément du premier jeu n’est pas dans le deuxième jeu.|
|isSubset (|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du premier jeu figurent dans le deuxième jeu.|
|isSuperset|-|-|-|-|O (M &#42; log N)|Retourne `true` si tous les éléments du second jeu figurent dans le premier jeu.|
|ITER|O(N)|O(N)|O(N)|O(N)|O(N)|Applique la fonction donnée à chaque élément de la collection.|
|iteri,|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à chaque élément de la collection. L’entier qui est passé à la fonction indique l’index de l’élément.|
|iteri2|O(N)|O(N)|-|-|-|Applique la fonction donnée à une paire d’éléments qui sont extraits de l’index correspondant dans deux tableaux. L’entier passé à la fonction indique l’index des éléments. Les deux tableaux doivent avoir la même longueur.|
|iter2|O(N)|O(N)|O(N)|-|-|Applique la fonction donnée à une paire d’éléments qui sont extraits de l’index correspondant dans deux tableaux. Les deux tableaux doivent avoir la même longueur.|
|last|O(1)|O(N)|O(N)|-|-|Retourne le dernier élément de la collection applicable.|
|length|O(1)|O(N)|O(N)|-|-|Retourne le nombre d’éléments dans la collection.|
|map|O(N)|O(N)|O(1)|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée à chaque élément du tableau.|
|map2|O(N)|O(N)|O(1)|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des deux collections. Les deux tableaux d’entrée doivent avoir la même longueur.|
|MaP3|-|O(N)|-|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des trois collections simultanément.|
|Protocole|O(N)|O(N)|O(N)|-|-|Génère un tableau dont les éléments sont les résultats de l’application de la fonction donnée à chaque élément du tableau. L’index d’entiers passé à la fonction indique l’index de l’élément en cours de transformation.|
|mapi2|O(N)|O(N)|-|-|-|Génère une collection dont les éléments sont les résultats de l’application de la fonction donnée aux éléments correspondants des deux collections par paire, en passant également l’index des éléments. Les deux tableaux d’entrée doivent avoir la même longueur.|
|max|O(N)|O(N)|O(N)|-|-|Retourne le plus grand élément de la collection, comparé à l’aide de l’opérateur [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) .|
|maxBy|O(N)|O(N)|O(N)|-|-|Retourne le plus grand élément de la collection, comparé en utilisant [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) sur le résultat de la fonction.|
|maxElement (|-|-|-|-|O (log N)|Retourne le plus grand élément du jeu en fonction de l’ordre utilisé pour le jeu.|
|min|O(N)|O(N)|O(N)|-|-|Retourne l’élément le moins dans la collection, comparé à l’aide de l’opérateur [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) .|
|minBy|O(N)|O(N)|O(N)|-|-|Retourne l’élément le moins dans la collection, comparé à l’aide de l’opérateur [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) sur le résultat de la fonction.|
|minElement (|-|-|-|-|O (log N)|Retourne l’élément le plus bas dans le jeu en fonction de l’ordre utilisé pour le jeu.|
|ofArray|-|O(N)|O(1)|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que le tableau donné.|
|ofList|O(N)|-|O(1)|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que la liste donnée.|
|ofSeq|O(N)|O(N)|-|O(N)|O(N)|Crée une collection qui contient les mêmes éléments que la séquence donnée.|
|séparées|-|-|O(N)|-|-|Retourne une séquence de chaque élément de la séquence d’entrée et son prédécesseur, à l’exception du premier élément, qui est retourné uniquement comme prédécesseur du deuxième élément.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Fractionne la collection en deux collections. La première collection contient les éléments pour lesquels le prédicat donné retourne `true`, et la deuxième collection contient les éléments pour lesquels le prédicat donné retourne `false`.|
|permute|O(N)|O(N)|-|-|-|Retourne un tableau avec tous les éléments permutés en fonction de la permutation spécifiée.|
|reprend|O(N)|O(N)|O(N)|O (log N)|-|Applique la fonction donnée à des éléments successifs, en retournant le premier résultat où la fonction retourne Some. Si la fonction ne retourne jamais Some, `System.Collections.Generic.KeyNotFoundException` est déclenché.|
|readonly|-|-|O(N)|-|-|Crée un objet séquence qui délègue à l’objet séquence donné. Cette opération garantit qu’un cast de type ne peut pas redécouvrir et muter la séquence d’origine. Par exemple, si un tableau est donné, la séquence retournée retourne les éléments du tableau, mais vous ne pouvez pas effectuer un cast de l’objet de séquence retourné en tableau.|
|reduce|O(N)|O(N)|O(N)|-|-|Applique une fonction à chaque élément de la collection, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Cette fonction commence par appliquer la fonction aux deux premiers éléments, passe ce résultat dans la fonction avec le troisième élément, et ainsi de suite. La fonction retourne le résultat final.|
|reduceBack,|O(N)|O(N)|-|-|-|Applique une fonction à chaque élément de la collection, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Si la fonction d’entrée est f et que les éléments sont i0... Dans, cette fonction calcule f i0 (... (f dans-1 dans)).|
|remove|-|-|-|O (log N)|O (log N)|Supprime un élément du domaine du mappage. Aucune exception n’est levée si l’élément n’est pas présent.|
|réplique|-|O(N)|-|-|-|Crée une liste d’une longueur spécifiée avec chaque élément défini sur la valeur donnée.|
|Rev|O(N)|O(N)|-|-|-|Retourne une nouvelle liste avec les éléments dans l’ordre inverse.|
|vérifier|O(N)|O(N)|O(N)|-|-|Applique une fonction à chaque élément de la collection, en utilisant un thread d’un argument d’accumulation par le biais du calcul. Cette opération applique la fonction au deuxième argument et au premier élément de la liste. L’opération passe ensuite ce résultat dans la fonction avec le deuxième élément, et ainsi de suite. Enfin, l’opération retourne la liste des résultats intermédiaires et le résultat final.|
|scanBack|O(N)|O(N)|-|-|-|Ressemble à l’opération foldBack, mais retourne les résultats intermédiaires et finaux.|
|singleton|-|-|O(1)|-|O(1)|Retourne une séquence qui produit un seul élément.|
|set|O(1)|-|-|-|-|Affecte la valeur spécifiée à un élément d’un tableau.|
|skip|-|-|O(N)|-|-|Retourne une séquence qui ignore N éléments de la séquence sous-jacente, puis produit les éléments restants de la séquence.|
|skipWhile|-|-|O(N)|-|-|Retourne une séquence qui, lorsqu’elle est itérée, ignore les éléments de la séquence sous-jacente pendant que le prédicat donné retourne `true` puis produit les éléments restants de la séquence.|
|sort|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|O (N log N)|O (N log N)|-|-|Trie la collection par valeur d’élément. Les éléments sont comparés à l’aide de [compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|O (N log N)|O (N log N)|-|-|Trie la liste donnée à l’aide des clés fournies par la projection donnée. Les clés sont comparées à l’aide de la [comparaison](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|-|-|-|-|Trie les éléments d’un tableau en le mutant sur place et en utilisant la fonction de comparaison donnée. Les éléments sont comparés à l’aide de la [comparaison](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|-|-|-|-|Trie les éléments d’un tableau en le mutant sur place et en utilisant la projection donnée pour les clés. Les éléments sont comparés à l’aide de la [comparaison](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|-|-|-|-|Trie les éléments d’un tableau en le mutant sur place et en utilisant la fonction de comparaison donnée comme ordre.|
|sortWith|Moyenne O (N log N)<br /><br />O (N ^ 2) pire cas|O (N log N)|-|-|-|Trie les éléments d’une collection, en utilisant la fonction de comparaison donnée comme ordre et en retournant une nouvelle collection.|
|sub|O(N)|-|-|-|-|Génère un tableau qui contient la sous-plage donnée spécifiée par l’index de départ et la longueur.|
|Sum|O(N)|O(N)|O(N)|-|-|Retourne la somme des éléments de la collection.|
|sumBy|O(N)|O(N)|O(N)|-|-|Retourne la somme des résultats générés en appliquant la fonction à chaque élément de la collection.|
|comporte|-|O(1)|-|-|-|Retourne la liste sans son premier élément.|
|take|-|-|O(N)|-|-|Retourne les éléments de la séquence jusqu’à un nombre spécifié.|
|takeWhile|-|-|O(1)|-|-|Retourne une séquence qui, lorsqu’elle est itérée, produit les éléments de la séquence sous-jacente pendant que le prédicat donné retourne `true`, puis ne retourne plus d’éléments.|
|toArray|-|O(N)|O(N)|O(N)|O(N)|Crée un tableau à partir de la collection donnée.|
|toList|O(N)|-|O(N)|O(N)|O(N)|Crée une liste à partir de la collection donnée.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Crée une séquence à partir de la collection donnée.|
|truncate|-|-|O(1)|-|-|Retourne une séquence qui, lorsqu’elle est énumérée, ne retourne pas plus de N éléments.|
|tryFind|O(N)|O(N)|O(N)|O (log N)|-|Recherche un élément qui satisfait un prédicat donné.|
|tryFindIndex|O(N)|O(N)|O(N)|-|-|Recherche le premier élément qui satisfait un prédicat donné et retourne l’index de l’élément correspondant, ou `None` si aucun élément de ce type n’existe.|
|tryFindKey|-|-|-|O (log N)|-|Retourne la clé du premier mappage de la collection qui répond au prédicat donné, ou retourne `None` si aucun élément de ce type n’existe.|
|tryPick,|O(N)|O(N)|O(N)|O (log N)|-|Applique la fonction donnée à des éléments successifs, en retournant le premier résultat où la fonction retourne `Some` pour une certaine valeur. Si aucun élément de ce type n’existe, l’opération retourne `None`.|
|dérouler|-|-|O(N)|-|-|Retourne une séquence qui contient les éléments générés par le calcul donné.|
|union|-|-|-|-|O (M &#42; log N)|Calcule l’Union des deux jeux.|
|unionMany (|-|-|-|-|O (N1 &#42; N2...)|Calcule l’Union d’une séquence de jeux.|
|unzip|O(N)|O(N)|O(N)|-|-|Divise une liste de paires en deux listes.|
|unzip3|O(N)|O(N)|O(N)|-|-|Divise une liste de triples en trois listes.|
|fenêtrées|-|-|O(N)|-|-|Retourne une séquence qui produit des fenêtres défilantes de contenant des éléments qui sont dessinés à partir de la séquence d’entrée. Chaque fenêtre est retournée sous la forme d’un tableau actualisé.|
|zip|O(N)|O(N)|O(N)|-|-|Combine les deux collections en une liste de paires. Les deux listes doivent avoir des longueurs égales.|
|zip3|O(N)|O(N)|O(N)|-|-|Combine les trois collections en une liste de triples. Les listes doivent avoir des longueurs égales.|

## <a name="see-also"></a>Voir aussi

- [Types F#](fsharp-types.md)
- [Informations de référence sur le langage F#](index.md)
