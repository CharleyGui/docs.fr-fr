---
title: Regrouper les résultats d’une requête (LINQ en C#)
description: Découvrez comment regrouper les résultats à l’aide de LINQ en C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688460"
---
# <a name="group-query-results"></a>Regrouper les résultats d’une requête

Le regroupement est l’une des fonctionnalités les plus puissantes de LINQ. Les exemples suivants montrent comment regrouper des données de différentes manières :

- Selon une propriété

- Selon la première lettre d’une propriété de chaîne

- Selon une plage numérique calculée

- Selon un prédicat booléen ou une autre expression

- Selon une clé composée

En outre, les deux dernières requêtes projettent leurs résultats dans un nouveau type anonyme qui contient uniquement le prénom et le nom de l’étudiant. Pour plus d’informations, consultez [group, clause](../language-reference/keywords/group-clause.md).

## <a name="example"></a> Exemple

Tous les exemples de cette rubrique utilisent les classes d’assistance et les sources de données suivantes.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a> Exemple

L’exemple suivant montre comment regrouper des éléments source en utilisant une propriété de l’élément comme clé de groupe. Dans ce cas, la clé est un `string`, qui correspond au nom de l’étudiant. Il est également possible d’utiliser une sous-chaîne comme clé. L’opération de regroupement utilise le comparateur d’égalité par défaut pour le type.

Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySingleProperty()`.

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a> Exemple

L’exemple suivant montre comment regrouper des éléments source en utilisant autre chose qu’une propriété de l’objet comme clé de groupe. Dans cet exemple, la clé est la première lettre du nom de l’étudiant.

Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySubstring()`.

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a> Exemple

L’exemple suivant montre comment regrouper des éléments source en utilisant une plage numérique comme clé de groupe. La requête projette ensuite les résultats dans un type anonyme qui contient uniquement le prénom et le nom de l’étudiant, ainsi que la plage de centiles à laquelle appartient l’étudiant. Un type anonyme est utilisé, car il n’est pas nécessaire d’utiliser l’intégralité de l’objet `Student` pour afficher les résultats. `GetPercentile` est une fonction d’assistance qui calcule un centile à partir de la note moyenne obtenue par l’étudiant. La méthode retourne un entier compris entre 0 et 10.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByRange()`.

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a> Exemple

L’exemple suivant montre comment regrouper des éléments source en utilisant une expression de comparaison booléenne. Dans cet exemple, l’expression booléenne teste si la note moyenne d’un étudiant est supérieure à 75. Comme dans les exemples précédents, les résultats sont projetés dans un type anonyme, car il n’est pas nécessaire d’avoir l’élément source complet. Notez que les propriétés du type anonyme deviennent des propriétés du membre `Key` et sont accessibles par nom lorsque la requête est exécutée.

Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByBoolean()`.

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser un type anonyme pour encapsuler une clé qui contient plusieurs valeurs. Dans cet exemple, la première valeur de clé est la première lettre du nom de l’étudiant. La deuxième valeur de clé est une valeur booléenne qui spécifie si l’étudiant a obtenu une note supérieure à 85 au premier examen. Vous pouvez organiser les groupes selon n’importe quelle propriété de la clé.

Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByCompositeKey()`.

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [Requête intégrée linguistique (LINQ)](index.md)
- [group, clause](../language-reference/keywords/group-clause.md)
- [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)
- [Effectuer une sous-querie sur une opération de regroupement](perform-a-subquery-on-a-grouping-operation.md)
- [Créer un groupe imbriqué](create-a-nested-group.md)
- [Regrouper les données](../programming-guide/concepts/linq/grouping-data.md)
