---
title: 'Comment : créer une variable'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 2a2b5b8bef3b66f9727f0e65b61882186c007e94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353630"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Comment : créer une variable (Visual Basic)

Vous créez une variable avec une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Pour créer une variable

1. Déclarez la variable dans une instruction `Dim`.

    ```vb
    Dim newCustomer
    ```

2. Inclure des spécifications pour les caractéristiques de la variable, telles que [Private](../../../../visual-basic/language-reference/modifiers/private.md), [static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Pour plus d’informations, consultez [caractéristiques des éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Vous n’avez pas besoin du mot clé `Dim` si vous utilisez d’autres mots clés dans la déclaration.

3. Suivez les spécifications avec le nom de la variable, qui doit suivre Visual Basic règles et conventions. Pour plus d’informations, consultez [noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Suivez le nom avec la clause [As](../../../../visual-basic/language-reference/statements/as-clause.md) pour spécifier le type de données de la variable.

    ```vb
    Public Static newCustomer As Customer
    ```

    Si vous ne spécifiez pas le type de données, il utilise la valeur par défaut : `Object`.

5. Suivez la clause `As` avec un signe égal (`=`) et suivez le signe égal avec la valeur initiale de la variable.

    Visual Basic affecte la valeur spécifiée à la variable chaque fois qu’il exécute l’instruction `Dim`. Si vous ne spécifiez pas de valeur initiale, Visual Basic affecte la valeur initiale par défaut pour le type de données de la variable lorsqu’il entre pour la première fois dans le code qui contient l’instruction `Dim`.

    Si la variable est un type référence, vous pouvez créer une instance de sa classe en incluant le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) dans la clause `As`. Si vous n’utilisez pas `New`, la valeur initiale de la variable est [Nothing](../../../../visual-basic/language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Voir aussi

- [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Instructions](../../../../visual-basic/language-reference/statements/index.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
