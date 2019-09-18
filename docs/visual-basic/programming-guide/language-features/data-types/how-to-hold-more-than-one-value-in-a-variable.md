---
title: 'Procédure : Contenir plusieurs valeurs dans une variable (Visual Basic)'
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054195"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Procédure : Contenir plusieurs valeurs dans une variable (Visual Basic)

Une variable contient plusieurs valeurs si vous la déclarez comme étant d’un *type de données composite*.

Les [types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluent des structures, des tableaux et des classes. Une variable d’un type de données composite peut contenir une combinaison de types de données élémentaires et d’autres types composites. Les structures et les classes peuvent contenir du code ainsi que des données.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Pour stocker plusieurs valeurs dans une variable

1. Déterminez le type de données composite que vous souhaitez utiliser pour votre variable.

2. Si le type de données composite n’est pas déjà défini, définissez-le afin que votre variable puisse l’utiliser.

    - Définissez une structure avec une [instruction structure](../../../../visual-basic/language-reference/statements/structure-statement.md).

    - Définissez un tableau avec une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

    - Définissez une classe avec une [instruction de classe](../../../../visual-basic/language-reference/statements/class-statement.md).

3. Déclarez votre variable avec `Dim` une instruction.

4. Suivez le nom de la variable `As` avec une clause.

5. Suivez le `As` mot clé avec le nom du type de données composite approprié.

## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
