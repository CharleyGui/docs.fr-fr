---
title: 'Procédure : Accélérer l’accès à un objet avec un chemin d’accès de qualification long (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631100"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Procédure : Accélérer l’accès à un objet avec un chemin d’accès de qualification long (Visual Basic)

Si vous accédez fréquemment à un objet qui requiert un chemin d’accès de qualification de plusieurs méthodes et propriétés, vous pouvez accélérer votre code en ne répétant pas le chemin d’accès de qualification.

Vous pouvez éviter de répéter le chemin d’accès de qualification de deux manières. Vous pouvez assigner l’objet à une variable, ou vous pouvez l’utiliser `With`dans un... `End With` bloquer.

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Pour accélérer l’accès à un objet très qualifié en l’assignant à une variable

1. Déclarez une variable du type de l’objet auquel vous accédez fréquemment. Spécifiez le chemin d’accès de qualification dans la partie initialisation de la déclaration.

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. Utilisez la variable pour accéder aux membres de l’objet.

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Pour accélérer l’accès à un objet très qualifié à l’aide d’un avec... Terminer par un bloc

1. Placez le chemin d’accès de `With` qualification dans une instruction.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Accédez aux membres de l’objet à `With` l’intérieur du bloc `End With` , avant l’instruction.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With (instruction)](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
