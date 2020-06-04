---
title: 'Comment : assigner un tableau à un autre tableau'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413077"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Comment : assigner un tableau à un autre tableau (Visual Basic)

Étant donné que les tableaux sont des objets, vous pouvez les utiliser dans des instructions d’assignation comme d’autres types d’objets. Une variable de tableau contient un pointeur vers les données qui constituent les éléments de tableau et les informations de rang et de longueur, et une assignation copie uniquement ce pointeur.

### <a name="to-assign-one-array-to-another-array"></a>Pour assigner un tableau à un autre tableau

1. Assurez-vous que les deux tableaux ont le même rang (nombre de dimensions) et les types de données d’éléments compatibles.

2. Utilisez une instruction d’assignation standard pour assigner le tableau source au tableau de destination. Ne suivez pas le nom d’un tableau avec des parenthèses.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Lorsque vous affectez un tableau à un autre, les règles suivantes s’appliquent :

- **Égalité des rangs.** Le rang (nombre de dimensions) du tableau de destination doit être le même que celui du tableau source.

  Si les rangs des deux tableaux sont égaux, les dimensions n’ont pas besoin d’être égales. Le nombre d’éléments d’une dimension donnée peut changer pendant l’assignation.

- **Types d’éléments.** Soit les deux tableaux doivent avoir des éléments de *type référence* , soit les deux tableaux doivent avoir des éléments de *type valeur* . Pour plus d'informations, consultez [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).

  - Si les deux tableaux ont des éléments de type valeur, les types de données d’élément doivent être exactement les mêmes. La seule exception à cela est que vous pouvez assigner un tableau d' `Enum` éléments à un tableau du type de base de ce `Enum` .

  - Si les deux tableaux ont des éléments de type référence, le type d’élément source doit dériver du type d’élément de destination. Dans ce cas, les deux tableaux ont la même relation d’héritage que leurs éléments. C’est ce que l’on appelle la *covariance de tableau*.

Le compilateur signale une erreur si les règles ci-dessus ne sont pas respectées, par exemple si les types de données ne sont pas compatibles ou si les rangs sont inégaux. Vous pouvez ajouter la gestion des erreurs à votre code pour vous assurer que les tableaux sont compatibles avant de tenter une attribution. Vous pouvez également utiliser le mot clé d' [opérateur TryCast](../../../language-reference/operators/trycast-operator.md) si vous souhaitez éviter de lever une exception.

## <a name="see-also"></a>Voir aussi

- [Tableaux](index.md)
- [Résolution des problèmes de tableaux](troubleshooting-arrays.md)
- [Enum (instruction)](../../../language-reference/statements/enum-statement.md)
- [Conversions de tableau](../data-types/array-conversions.md)
