---
title: "'Optional' attendu"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873603"
---
# <a name="optional-expected"></a><span data-ttu-id="e5190-102">'Optional' attendu</span><span class="sxs-lookup"><span data-stu-id="e5190-102">'Optional' expected</span></span>

<span data-ttu-id="e5190-103">Un argument facultatif dans une déclaration de procédure est suivi d’un argument obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e5190-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="e5190-104">Chaque argument qui suit un argument facultatif doit également être facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5190-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="e5190-105">**ID d’erreur :** BC30202</span><span class="sxs-lookup"><span data-stu-id="e5190-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5190-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e5190-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e5190-107">Si l’argument est destiné à être requis, déplacez-le pour qu’il précède le premier argument facultatif dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="e5190-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="e5190-108">Si l’argument est destiné à être facultatif, utilisez le `Optional` mot clé.</span><span class="sxs-lookup"><span data-stu-id="e5190-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5190-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5190-109">See also</span></span>

- [<span data-ttu-id="e5190-110">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="e5190-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
