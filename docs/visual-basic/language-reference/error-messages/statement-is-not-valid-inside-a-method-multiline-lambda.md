---
title: Instruction non valide dans une méthode ou une expression lambda multiligne
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396244"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="f258f-102">Instruction non valide dans une méthode ou une expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="f258f-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="f258f-103">L’instruction n’est pas valide dans `Sub` une `Function` procédure de propriété,, `Get` ou `Set` .</span><span class="sxs-lookup"><span data-stu-id="f258f-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="f258f-104">Certaines instructions peuvent être placées au niveau du module ou de la classe.</span><span class="sxs-lookup"><span data-stu-id="f258f-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="f258f-105">D’autres, telles que `Option Strict` , doivent se trouver au niveau de l’espace de noms et précéder toutes les autres déclarations.</span><span class="sxs-lookup"><span data-stu-id="f258f-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="f258f-106">**ID d’erreur :** BC30024</span><span class="sxs-lookup"><span data-stu-id="f258f-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f258f-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f258f-107">To correct this error</span></span>  
  
- <span data-ttu-id="f258f-108">Supprimez l’instruction de la procédure.</span><span class="sxs-lookup"><span data-stu-id="f258f-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f258f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f258f-109">See also</span></span>

- [<span data-ttu-id="f258f-110">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="f258f-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="f258f-111">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="f258f-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="f258f-112">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="f258f-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="f258f-113">Instruction Set</span><span class="sxs-lookup"><span data-stu-id="f258f-113">Set Statement</span></span>](../statements/set-statement.md)
