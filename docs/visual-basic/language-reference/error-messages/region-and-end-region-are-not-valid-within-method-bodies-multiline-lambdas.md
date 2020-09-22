---
title: Les instructions « #Region » et « #End Region » ne sont pas valides dans le corps des méthodes ou les expressions lambda multiligne
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870888"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="fb3f6-102">Les instructions '#Region' et '#End Region' ne sont pas valides dans le corps des méthodes ou les expressions lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="fb3f6-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="fb3f6-103">Le `#Region` bloc doit être déclaré au niveau d’un classe, d’un module ou d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="fb3f6-104">Une région réductible peut inclure une ou plusieurs procédures, mais elle ne peut pas commencer ni se terminer à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="fb3f6-105">**ID d’erreur :** BC32025</span><span class="sxs-lookup"><span data-stu-id="fb3f6-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb3f6-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="fb3f6-106">To correct this error</span></span>  
  
1. <span data-ttu-id="fb3f6-107">Vérifiez que la procédure précédente est correctement terminée par une `End Function` instruction ou `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="fb3f6-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="fb3f6-108">Vérifiez que les `#Region` `#End Region` directives et se trouvent dans le même bloc de code.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3f6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb3f6-109">See also</span></span>

- [<span data-ttu-id="fb3f6-110">#Region directive</span><span class="sxs-lookup"><span data-stu-id="fb3f6-110">#Region Directive</span></span>](../directives/region-directive.md)
