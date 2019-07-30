---
title: 'Procédure : Déclarez une variable objet et assignez-lui un objet dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630871"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Procédure : Déclarez une variable objet et assignez-lui un objet dans Visual Basic

Vous déclarez une variable du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) en `As Object` spécifiant dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Vous assignez un objet à une telle variable en plaçant l’objet après le signe`=`égal () dans une instruction d’assignation ou une clause d’initialisation.

## <a name="example"></a>Exemple

L’exemple suivant déclare une `Object` variable et lui assigne l’instance actuelle.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Vous pouvez combiner la déclaration et l’assignation en initialisant la variable dans le cadre de sa déclaration. L’exemple suivant est équivalent à l’exemple précédent.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- une référence à l'espace de noms <xref:System>.

- Classe, structure ou module dans lequel placer l' `Dim` instruction.

- Procédure dans laquelle placer l’instruction d’assignation.

## <a name="see-also"></a>Voir aussi

- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
