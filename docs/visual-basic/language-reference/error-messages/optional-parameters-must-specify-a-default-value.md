---
title: Les paramètres optionnels doivent spécifier une valeur par défaut
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 3718fe5c42c8af0948f3b5cb0d120c6876c6f98f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162451"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a>BC30812 : les paramètres facultatifs doivent spécifier une valeur par défaut

Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.

**ID d’erreur :** BC30812

## <a name="example"></a> Exemple

L’exemple suivant génère l’BC30812 :

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Spécifiez les valeurs par défaut des paramètres facultatifs :

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a>Voir aussi

- [Facultatif](../modifiers/optional.md)
