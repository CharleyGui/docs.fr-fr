---
title: 'Comment : créer une variable'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410527"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Comment : créer une variable (Visual Basic)

Vous créez une variable avec une [instruction Dim](../../../language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Pour créer une variable

1. Déclarez la variable dans une `Dim` instruction.

    ```vb
    Dim newCustomer
    ```

2. Inclure des spécifications pour les caractéristiques de la variable, telles que [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)ou [WithEvents](../../../language-reference/modifiers/withevents.md). Pour plus d’informations, consultez [caractéristiques des éléments déclarés](../declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Vous n’avez pas besoin du `Dim` mot clé si vous utilisez d’autres mots clés dans la déclaration.

3. Suivez les spécifications avec le nom de la variable, qui doit suivre Visual Basic règles et conventions. Pour plus d’informations, consultez [noms d’éléments déclarés](../declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Suivez le nom avec la clause [As](../../../language-reference/statements/as-clause.md) pour spécifier le type de données de la variable.

    ```vb
    Public Static newCustomer As Customer
    ```

    Si vous ne spécifiez pas le type de données, il utilise la valeur par défaut : `Object` .

5. Suivez la `As` clause avec un signe égal ( `=` ) et suivez le signe égal avec la valeur initiale de la variable.

    Visual Basic affecte la valeur spécifiée à la variable chaque fois qu’il exécute l' `Dim` instruction. Si vous ne spécifiez pas de valeur initiale, Visual Basic affecte la valeur initiale par défaut pour le type de données de la variable lorsqu’il entre pour la première fois dans le code qui contient l' `Dim` instruction.

    Si la variable est un type référence, vous pouvez créer une instance de sa classe en incluant le mot clé [New Operator](../../../language-reference/operators/new-operator.md) dans la `As` clause. Si vous n’utilisez pas `New` , la valeur initiale de la variable est [Nothing](../../../language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Voir aussi

- [Variables](index.md)
- [Déclaration de variable](variable-declaration.md)
- [Declared Element Names](../declared-elements/declared-element-names.md)
- [Caractéristiques des éléments déclarés](../declared-elements/declared-element-characteristics.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
- [Instructions](../../../language-reference/statements/index.md)
- [Inférence de type local](local-type-inference.md)
- [Instruction Option Infer](../../../language-reference/statements/option-infer-statement.md)
