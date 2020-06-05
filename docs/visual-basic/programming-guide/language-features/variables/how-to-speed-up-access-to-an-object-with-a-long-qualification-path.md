---
title: 'Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410410"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long (Visual Basic)

Si vous accédez fréquemment à un objet qui requiert un chemin d’accès de qualification de plusieurs méthodes et propriétés, vous pouvez accélérer votre code en ne répétant pas le chemin d’accès de qualification.

Vous pouvez éviter de répéter le chemin d’accès de qualification de deux manières. Vous pouvez assigner l’objet à une variable, ou vous pouvez l’utiliser dans un `With` bloc... `End With` .

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

1. Placez le chemin d’accès de qualification dans une `With` instruction.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Accédez aux membres de l’objet à l’intérieur du `With` bloc, avant l' `End With` instruction.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Voir aussi

- [Variables objets](object-variables.md)
- [With...End With (instruction)](../../../language-reference/statements/with-end-with-statement.md)
