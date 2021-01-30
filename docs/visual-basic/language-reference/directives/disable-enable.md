---
title: Directives d’activation et de désactivation
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217228"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="36dad-102">Directives #Disable et #Enable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36dad-102">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="36dad-103">Les `#Disable` `#Enable` directives et sont Visual Basic les directives de compilateur de code source.</span><span class="sxs-lookup"><span data-stu-id="36dad-103">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="36dad-104">Ils permettent de désactiver et de réactiver des avertissements spécifiques pour les régions de code.</span><span class="sxs-lookup"><span data-stu-id="36dad-104">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="36dad-105">Vous pouvez également désactiver et activer une liste de codes d’avertissement séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="36dad-105">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="36dad-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36dad-106">See also</span></span>

- [<span data-ttu-id="36dad-107">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36dad-107">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="36dad-108">Comment supprimer des avertissements d’analyse du code</span><span class="sxs-lookup"><span data-stu-id="36dad-108">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
