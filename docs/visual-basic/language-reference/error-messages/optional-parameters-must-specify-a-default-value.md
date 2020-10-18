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
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="726be-102">BC30812 : les paramètres facultatifs doivent spécifier une valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="726be-102">BC30812: Optional parameters must specify a default value</span></span>

<span data-ttu-id="726be-103">Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="726be-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="726be-104">**ID d’erreur :** BC30812</span><span class="sxs-lookup"><span data-stu-id="726be-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="726be-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="726be-105">Example</span></span>

<span data-ttu-id="726be-106">L’exemple suivant génère l’BC30812 :</span><span class="sxs-lookup"><span data-stu-id="726be-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="726be-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="726be-107">To correct this error</span></span>

<span data-ttu-id="726be-108">Spécifiez les valeurs par défaut des paramètres facultatifs :</span><span class="sxs-lookup"><span data-stu-id="726be-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="726be-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="726be-109">See also</span></span>

- [<span data-ttu-id="726be-110">Facultatif</span><span class="sxs-lookup"><span data-stu-id="726be-110">Optional</span></span>](../modifiers/optional.md)
