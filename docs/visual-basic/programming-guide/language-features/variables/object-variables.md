---
title: Variables objet
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351784"
---
# <a name="object-variables-in-visual-basic"></a>Variables objet dans Visual Basic

Outre le stockage direct des valeurs, une variable peut faire référence à un objet. Vous assignez un objet à une variable pour les mêmes raisons que vous attribuez une valeur à une variable :

- Un nom de variable est souvent plus concis et plus facile à mémoriser que le chemin complet des méthodes et propriétés nécessaires pour accéder à l’objet lui-même.

- L’utilisation d’une variable qui fait référence à un objet est plus efficace que l’accès répété à l’objet lui-même par le biais des méthodes ou propriétés nécessaires.

- Vous pouvez modifier une variable pour faire référence à d’autres objets pendant l’exécution de votre code.

## <a name="making-code-shorter"></a>Rendre le code plus concis

Vous pouvez utiliser des variables d’objet pour raccourcir le code que vous devez taper. L’exemple suivant utilise le chemin d’accès complet des méthodes et des propriétés pour accéder à un objet <xref:System.Windows.Forms.Control>.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Vous pouvez raccourcir ce code et accélérer l’exécution, si vous utilisez une variable objet pour le contrôle. Vous devez déclarer la variable objet avec la classe spécifique que vous souhaitez lui assigner (`Control` dans ce cas). Une fois que vous affectez un objet à la variable, vous pouvez le traiter exactement de la même façon que vous traitez l’objet auquel il fait référence. Vous pouvez définir ou récupérer les propriétés de l’objet ou utiliser l’une de ses méthodes. L’exemple suivant utilise une variable objet pour simplifier le code de l’exemple précédent.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Voir aussi

- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Guide pratique : accélérer l’accès à un objet comportant un chemin d’accès de qualification long](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
