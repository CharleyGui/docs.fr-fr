---
title: <type1> <typename> doit implémenter <methodname> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591593"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="7087a-102">\<type1 > ' \<typename > 'doit implémenter' \<methodname > 'pour l’interface' \<interfacename > '</span><span class="sxs-lookup"><span data-stu-id="7087a-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="7087a-103">Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure définie par l’interface.</span><span class="sxs-lookup"><span data-stu-id="7087a-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="7087a-104">Chaque membre de l’interface doit être implémenté.</span><span class="sxs-lookup"><span data-stu-id="7087a-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="7087a-105">**ID d’erreur :** BC30149</span><span class="sxs-lookup"><span data-stu-id="7087a-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7087a-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7087a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="7087a-107">Déclarez une procédure avec les mêmes nom et signature que ceux définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="7087a-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="7087a-108">Veillez à inclure au moins l’instruction `End Function` ou `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="7087a-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="7087a-109">Ajoutez une clause `Implements` à la fin de l’instruction `Function` ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="7087a-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="7087a-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7087a-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7087a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7087a-111">See also</span></span>

- [<span data-ttu-id="7087a-112">Implements (instruction)</span><span class="sxs-lookup"><span data-stu-id="7087a-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="7087a-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7087a-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
