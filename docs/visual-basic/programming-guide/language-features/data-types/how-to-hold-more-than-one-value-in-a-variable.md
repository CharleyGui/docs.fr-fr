---
title: 'Procédure : Stocker plusieurs valeurs dans une variable'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393894"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Comment : stocker plusieurs valeurs dans une variable (Visual Basic)

Une variable contient plusieurs valeurs si vous la déclarez comme étant d’un *type de données composite*.

Les [types de données composites](composite-data-types.md) incluent des structures, des tableaux et des classes. Une variable d’un type de données composite peut contenir une combinaison de types de données élémentaires et d’autres types composites. Les structures et les classes peuvent contenir du code ainsi que des données.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Pour stocker plusieurs valeurs dans une variable

1. Déterminez le type de données composite que vous souhaitez utiliser pour votre variable.

2. Si le type de données composite n’est pas déjà défini, définissez-le afin que votre variable puisse l’utiliser.

    - Définissez une structure avec une [instruction structure](../../../language-reference/statements/structure-statement.md).

    - Définissez un tableau avec une [instruction Dim](../../../language-reference/statements/dim-statement.md).

    - Définissez une classe avec une [instruction de classe](../../../language-reference/statements/class-statement.md).

3. Déclarez votre variable avec une `Dim` instruction.

4. Suivez le nom de la variable avec une `As` clause.

5. Suivez le `As` mot clé avec le nom du type de données composite approprié.

## <a name="see-also"></a>Voir aussi

- [Types de données](../../../language-reference/data-types/index.md)
- [Caractères de type](type-characters.md)
- [Types de données composites](composite-data-types.md)
- [Structures](structures.md)
- [Tableaux](../arrays/index.md)
- [Objets et classes](../objects-and-classes/index.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
