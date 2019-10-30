---
title: Les paramètres optionnels doivent spécifier une valeur par défaut
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040926"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="f8e68-102">Les paramètres optionnels doivent spécifier une valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f8e68-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="f8e68-103">Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="f8e68-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="f8e68-104">**ID d’erreur :** BC30812</span><span class="sxs-lookup"><span data-stu-id="f8e68-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="f8e68-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8e68-105">Example</span></span>

<span data-ttu-id="f8e68-106">L’exemple suivant génère l’BC30812 :</span><span class="sxs-lookup"><span data-stu-id="f8e68-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="f8e68-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f8e68-107">To correct this error</span></span>

<span data-ttu-id="f8e68-108">Spécifiez les valeurs par défaut des paramètres facultatifs :</span><span class="sxs-lookup"><span data-stu-id="f8e68-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="f8e68-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8e68-109">See also</span></span>

- [<span data-ttu-id="f8e68-110">Optional</span><span class="sxs-lookup"><span data-stu-id="f8e68-110">Optional</span></span>](../modifiers/optional.md)
