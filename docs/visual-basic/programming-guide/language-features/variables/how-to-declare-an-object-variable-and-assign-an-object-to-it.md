---
title: 'Comment : déclarer une variable objet et lui assigner un objet'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352902"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic

Vous déclarez une variable du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) en spécifiant `As Object` dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Vous assignez un objet à une telle variable en plaçant l’objet après le signe égal (`=`) dans une instruction d’assignation ou une clause d’initialisation.

## <a name="example"></a>Exemple

L’exemple suivant déclare une variable `Object` et lui affecte l’instance actuelle.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Vous pouvez combiner la déclaration et l’assignation en initialisant la variable dans le cadre de sa déclaration. L’exemple suivant est équivalent à l’exemple précédent.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- une référence à l'espace de noms <xref:System>.

- Classe, structure ou module dans lequel placer l’instruction `Dim`.

- Procédure dans laquelle placer l’instruction d’assignation.

## <a name="see-also"></a>Voir aussi

- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
