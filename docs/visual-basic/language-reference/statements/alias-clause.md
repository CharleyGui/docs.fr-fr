---
title: Alias (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 77d4685f242864842e5a84b3a3de3ba1793e9aa4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866679"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="83ab0-102">Alias, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83ab0-102">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="83ab0-103">Indique qu’une procédure externe a un autre nom dans sa DLL.</span><span class="sxs-lookup"><span data-stu-id="83ab0-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83ab0-104">Notes</span><span class="sxs-lookup"><span data-stu-id="83ab0-104">Remarks</span></span>  

 <span data-ttu-id="83ab0-105">Le `Alias` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="83ab0-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="83ab0-106">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="83ab0-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="83ab0-107">Dans l’exemple suivant, le `Alias` mot clé est utilisé pour fournir le nom de la fonction dans advapi32.dll, `GetUserNameA` , qui `getUserName` est utilisé à la place de dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="83ab0-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="83ab0-108">La fonction `getUserName` est appelée dans Sub `getUser` , qui affiche le nom de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="83ab0-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="83ab0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83ab0-109">See also</span></span>

- [<span data-ttu-id="83ab0-110">Mots clés</span><span class="sxs-lookup"><span data-stu-id="83ab0-110">Keywords</span></span>](../keywords/index.md)
