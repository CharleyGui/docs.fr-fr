---
title: "'<typename>' ne peut pas hériter de <type> '<basetypename>' car il étend l'accès du <type> de base en dehors de l'assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402770"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="e6a03-102">'\<typename>' ne peut pas hériter de \<type> '\<basetypename>' car il étend l'accès du \<type> de base en dehors de l'assembly</span><span class="sxs-lookup"><span data-stu-id="e6a03-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="e6a03-103">Une classe ou une interface hérite d’une classe de base ou d’une interface, mais a un niveau d’accès moins restrictif.</span><span class="sxs-lookup"><span data-stu-id="e6a03-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="e6a03-104">Par exemple, une `Public` interface hérite d’une `Friend` interface ou une `Protected` classe hérite d’une `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="e6a03-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="e6a03-105">Cela expose l’interface ou la classe de base à l’accès au-delà du niveau prévu.</span><span class="sxs-lookup"><span data-stu-id="e6a03-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="e6a03-106">**ID d’erreur :** BC30910</span><span class="sxs-lookup"><span data-stu-id="e6a03-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e6a03-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e6a03-107">To correct this error</span></span>  
  
- <span data-ttu-id="e6a03-108">Modifiez le niveau d’accès de la classe ou de l’interface dérivée pour qu’il soit au moins aussi restrictif que celui de la classe ou de l’interface de base.</span><span class="sxs-lookup"><span data-stu-id="e6a03-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="e6a03-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="e6a03-109">-or-</span></span>  
  
- <span data-ttu-id="e6a03-110">Si vous avez besoin d’un niveau d’accès moins restrictif, supprimez l' `Inherits` instruction.</span><span class="sxs-lookup"><span data-stu-id="e6a03-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="e6a03-111">Vous ne pouvez pas hériter d’une classe ou d’une interface de base plus restreinte.</span><span class="sxs-lookup"><span data-stu-id="e6a03-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a03-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6a03-112">See also</span></span>

- [<span data-ttu-id="e6a03-113">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="e6a03-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="e6a03-114">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="e6a03-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="e6a03-115">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="e6a03-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="e6a03-116">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6a03-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
