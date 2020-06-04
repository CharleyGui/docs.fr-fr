---
title: Alias (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408469"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="97d44-102">Alias, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97d44-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="97d44-103">Indique qu’une procédure externe a un autre nom dans sa DLL.</span><span class="sxs-lookup"><span data-stu-id="97d44-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d44-104">Notes</span><span class="sxs-lookup"><span data-stu-id="97d44-104">Remarks</span></span>  
 <span data-ttu-id="97d44-105">Le `Alias` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="97d44-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="97d44-106">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="97d44-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="97d44-107">Dans l’exemple suivant, le `Alias` mot clé est utilisé pour fournir le nom de la fonction dans advapi32. dll, `GetUserNameA` , qui `getUserName` est utilisé à la place de dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="97d44-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="97d44-108">La fonction `getUserName` est appelée dans Sub `getUser` , qui affiche le nom de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="97d44-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="97d44-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d44-109">See also</span></span>

- [<span data-ttu-id="97d44-110">Mots clés</span><span class="sxs-lookup"><span data-stu-id="97d44-110">Keywords</span></span>](../keywords/index.md)
