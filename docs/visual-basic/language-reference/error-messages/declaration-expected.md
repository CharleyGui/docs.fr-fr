---
title: Déclaration attendue
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: ee8f1f9ec26dc6c938f0b412dfe30832e3cfe165
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874521"
---
# <a name="declaration-expected"></a><span data-ttu-id="07011-102">Déclaration attendue</span><span class="sxs-lookup"><span data-stu-id="07011-102">Declaration expected</span></span>

<span data-ttu-id="07011-103">Une instruction non déclarative, telle qu’une instruction d’assignation ou de boucle, se produit en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="07011-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="07011-104">Seules les déclarations sont autorisées en dehors des procédures.</span><span class="sxs-lookup"><span data-stu-id="07011-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="07011-105">Un élément de programmation est également déclaré sans mot clé de déclaration, tel que `Dim` ou `Const` .</span><span class="sxs-lookup"><span data-stu-id="07011-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="07011-106">**ID d’erreur :** BC30188</span><span class="sxs-lookup"><span data-stu-id="07011-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07011-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="07011-107">To correct this error</span></span>  
  
- <span data-ttu-id="07011-108">Déplacez l’instruction not Declarative dans le corps d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="07011-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="07011-109">Commencez la déclaration par un mot clé de déclaration approprié.</span><span class="sxs-lookup"><span data-stu-id="07011-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="07011-110">Assurez-vous qu’un mot clé de déclaration n’est pas mal orthographié.</span><span class="sxs-lookup"><span data-stu-id="07011-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07011-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07011-111">See also</span></span>

- [<span data-ttu-id="07011-112">Procédures</span><span class="sxs-lookup"><span data-stu-id="07011-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="07011-113">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="07011-113">Dim Statement</span></span>](../statements/dim-statement.md)
