---
title: Dimensions du tableau
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413102"
---
# <a name="array-dimensions-in-visual-basic"></a>Dimensions du tableau dans Visual Basic

Une *dimension* est un sens dans lequel vous pouvez faire varier la spécification des éléments d’un tableau. Un tableau qui contient le total des ventes pour chaque jour du mois a une dimension (le jour du mois). Un tableau qui contient le total des ventes par département pour chaque jour du mois a deux dimensions (le numéro de service et le jour du mois). Le nombre de dimensions d’un tableau est appelé son *rang*.

> [!NOTE]
> Vous pouvez utiliser la <xref:System.Array.Rank%2A> propriété pour déterminer le nombre de dimensions d’un tableau.

## <a name="working-with-dimensions"></a>Utilisation de dimensions

Vous spécifiez un élément d’un tableau en fournissant un *index* ou un *indice* pour chacune de ses dimensions. Les éléments sont contigus le long de chaque dimension à partir de l’index 0 jusqu’à l’index le plus élevé pour cette dimension.

Les illustrations suivantes montrent la structure conceptuelle des tableaux avec des rangs différents. Chaque élément dans les illustrations affiche les valeurs d’index qui y accèdent. Par exemple, vous pouvez accéder au premier élément de la deuxième ligne du tableau à deux dimensions en spécifiant des index `(1, 0)` .

![Diagramme qui montre un tableau unidimensionnel.](./media/array-dimensions/one-dimensional-array.gif)

![Diagramme qui montre un tableau à deux dimensions.](./media/array-dimensions/two-dimensional-array.gif)

![Diagramme qui montre un tableau à trois dimensions.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a>Une dimension

De nombreux tableaux n’ont qu’une seule dimension, comme le nombre de personnes de chaque âge. La seule condition requise pour spécifier un élément est l’âge pour lequel cet élément contient le nombre. Par conséquent, un tel tableau utilise un seul index. L’exemple suivant déclare une variable qui doit contenir un *tableau unidimensionnel* de nombres d’âge pour les âges de 0 à 120.

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a>Deux dimensions

Certains tableaux ont deux dimensions, telles que le nombre de bureaux à chaque étage de chaque bâtiment sur un campus. La spécification d’un élément nécessite à la fois le numéro de bâtiment et le plancher, et chaque élément contient le nombre pour cette combinaison de construction et d’étage. Par conséquent, un tel tableau utilise deux index. L’exemple suivant déclare une variable destinée à contenir un *tableau à deux dimensions* de nombres de bureaux, pour les bâtiments de 0 à 40 et les étages de 0 à 5.

```vb
Dim officeCounts(40, 5) As Byte
```

Un tableau à deux dimensions est également appelé *tableau rectangulaire*.

### <a name="three-dimensions"></a>Trois dimensions

Quelques tableaux ont trois dimensions, telles que des valeurs dans un espace tridimensionnel. Ce type de tableau utilise trois index, qui dans ce cas représentent les coordonnées x, y et z de l’espace physique. L’exemple suivant déclare une variable qui doit contenir un *tableau à trois dimensions* de températures atmosphériques à différents points d’un volume tridimensionnel.

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a>Plus de trois dimensions

Bien qu’un tableau puisse avoir jusqu’à 32 dimensions, il est rare d’en avoir plus de trois.

> [!NOTE]
> Lorsque vous ajoutez des dimensions à un tableau, le stockage total requis par le tableau augmente considérablement, donc utilisez des tableaux multidimensionnels avec précaution.

## <a name="using-different-dimensions"></a>Utilisation de différentes dimensions

Supposons que vous souhaitez effectuer le suivi des montants des ventes pour chaque jour du mois présent. Vous pouvez déclarer un tableau unidimensionnel avec 31 éléments, un pour chaque jour du mois, comme le montre l’exemple suivant.

```vb
Dim salesAmounts(30) As Double
```

Supposons à présent que vous souhaitiez suivre les mêmes informations non seulement pour chaque jour du mois, mais également pour chaque mois de l’année. Vous pouvez déclarer un tableau à deux dimensions avec 12 lignes (pour les mois) et 31 colonnes (pour les jours), comme le montre l’exemple suivant.

```vb
Dim salesAmounts(11, 30) As Double
```

Supposons à présent que vous décidiez que votre tableau conserve les informations pendant plus d’un an. Si vous souhaitez effectuer le suivi des montants des ventes pendant 5 ans, vous pouvez déclarer un tableau à trois dimensions avec 5 couches, 12 lignes et 31 colonnes, comme le montre l’exemple suivant.

```vb
Dim salesAmounts(4, 11, 30) As Double
```

Notez que, étant donné que chaque index varie de 0 à son maximum, chaque dimension de `salesAmounts` est déclarée comme une valeur inférieure à la longueur requise pour cette dimension. Notez également que la taille du tableau augmente avec chaque nouvelle dimension. Les trois tailles dans les exemples précédents sont respectivement 31, 372 et 1 860 éléments.

> [!NOTE]
> Vous pouvez créer un tableau sans utiliser l' `Dim` instruction ou la `New` clause. Par exemple, vous pouvez appeler la <xref:System.Array.CreateInstance%2A> méthode, ou un autre composant peut passer votre code à un tableau créé de cette manière. Un tel tableau peut avoir une limite inférieure différente de 0. Vous pouvez toujours tester la limite inférieure d’une dimension à l’aide de la <xref:System.Array.GetLowerBound%2A> méthode ou de la `LBound` fonction.

## <a name="see-also"></a>Voir aussi

- [Tableaux](index.md)
- [Résolution des problèmes de tableaux](troubleshooting-arrays.md)
