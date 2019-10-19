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
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="c14ee-102">Les paramètres optionnels doivent spécifier une valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c14ee-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="c14ee-103">Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="c14ee-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="c14ee-104">**ID d’erreur :** BC30812</span><span class="sxs-lookup"><span data-stu-id="c14ee-104">**Error ID:** BC30812</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c14ee-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c14ee-105">To correct this error</span></span>

<span data-ttu-id="c14ee-106">Spécifiez les valeurs par défaut des paramètres facultatifs. par exemple :</span><span class="sxs-lookup"><span data-stu-id="c14ee-106">Specify default values for optional parameters; for example:</span></span>

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="c14ee-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c14ee-107">See also</span></span>

- [<span data-ttu-id="c14ee-108">Optional</span><span class="sxs-lookup"><span data-stu-id="c14ee-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
