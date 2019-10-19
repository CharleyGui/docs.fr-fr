---
title: Les paramètres optionnels doivent spécifier une valeur par défaut
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582133"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Les paramètres optionnels doivent spécifier une valeur par défaut

Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.

**ID d’erreur :** BC30812

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Spécifiez les valeurs par défaut des paramètres facultatifs. par exemple :

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a>Voir aussi

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
