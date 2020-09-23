---
title: Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: d159b9bb3a765a2fefe99fa15dff42e979fda9e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079137"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="1507d-102">Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source</span><span class="sxs-lookup"><span data-stu-id="1507d-102">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="1507d-103">Une opération cyclique a échoué.</span><span class="sxs-lookup"><span data-stu-id="1507d-103">A cyclic operation has failed.</span></span> <span data-ttu-id="1507d-104">Les opérations cycliques se répètent et, par conséquent, ne peuvent pas s’achever.</span><span class="sxs-lookup"><span data-stu-id="1507d-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="1507d-105">Par exemple, l’objet A peut essayer d’hériter de l’objet B qui hérite, à son tour, de l’objet A.</span><span class="sxs-lookup"><span data-stu-id="1507d-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1507d-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1507d-106">To correct this error</span></span>  
  
- <span data-ttu-id="1507d-107">Lors d’un héritage, vérifiez qu’il n’existe aucune référence cyclique.</span><span class="sxs-lookup"><span data-stu-id="1507d-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1507d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1507d-108">See also</span></span>

- [<span data-ttu-id="1507d-109">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="1507d-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="1507d-110">Utiliser des points d’arrêt dans le débogueur Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1507d-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
