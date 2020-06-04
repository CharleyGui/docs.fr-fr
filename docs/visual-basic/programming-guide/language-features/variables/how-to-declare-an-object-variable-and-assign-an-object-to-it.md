---
title: 'Guide pratique : déclarer une variable objet et lui affecter un objet'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410501"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic

Vous déclarez une variable du [type de données Object](../../../language-reference/data-types/object-data-type.md) en spécifiant `As Object` dans une [instruction Dim](../../../language-reference/statements/dim-statement.md). Vous assignez un objet à une telle variable en plaçant l’objet après le signe égal ( `=` ) dans une instruction d’assignation ou une clause d’initialisation.

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

## <a name="compile-the-code"></a>Compiler le code

Cet exemple nécessite :

- une référence à l'espace de noms <xref:System>.

- Classe, structure ou module dans lequel placer l' `Dim` instruction.

- Procédure dans laquelle placer l’instruction d’assignation.

## <a name="see-also"></a>Voir aussi

- [Déclaration de variable](variable-declaration.md)
- [Variables objets](object-variables.md)
- [Déclaration des variables objets](object-variable-declaration.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
- [Inférence de type local](local-type-inference.md)
- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
