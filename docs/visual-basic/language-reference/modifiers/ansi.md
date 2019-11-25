---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344739"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="93fde-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93fde-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="93fde-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span><span class="sxs-lookup"><span data-stu-id="93fde-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="93fde-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span><span class="sxs-lookup"><span data-stu-id="93fde-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="93fde-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span><span class="sxs-lookup"><span data-stu-id="93fde-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="93fde-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span><span class="sxs-lookup"><span data-stu-id="93fde-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="93fde-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span><span class="sxs-lookup"><span data-stu-id="93fde-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="93fde-108">It also affects how Visual Basic searches the external file for the external procedure name.</span><span class="sxs-lookup"><span data-stu-id="93fde-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="93fde-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span><span class="sxs-lookup"><span data-stu-id="93fde-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="93fde-110">If no character set modifier is specified, `Ansi` is the default.</span><span class="sxs-lookup"><span data-stu-id="93fde-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93fde-111">Notes</span><span class="sxs-lookup"><span data-stu-id="93fde-111">Remarks</span></span>  
 <span data-ttu-id="93fde-112">The `Ansi` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="93fde-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="93fde-113">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="93fde-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="93fde-114">Smart Device Developer Notes</span><span class="sxs-lookup"><span data-stu-id="93fde-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="93fde-115">This keyword is not supported.</span><span class="sxs-lookup"><span data-stu-id="93fde-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fde-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93fde-116">See also</span></span>

- [<span data-ttu-id="93fde-117">Auto</span><span class="sxs-lookup"><span data-stu-id="93fde-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="93fde-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="93fde-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="93fde-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="93fde-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
