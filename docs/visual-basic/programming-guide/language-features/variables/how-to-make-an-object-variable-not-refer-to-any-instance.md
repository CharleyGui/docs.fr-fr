---
title: "Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance"
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352892"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="ec8ef-102">Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec8ef-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="ec8ef-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="ec8ef-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="ec8ef-104">To disassociate an object variable from any object instance</span><span class="sxs-lookup"><span data-stu-id="ec8ef-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="ec8ef-105">Set the variable to `Nothing` in an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="ec8ef-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="ec8ef-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ec8ef-106">Robust Programming</span></span>  
 <span data-ttu-id="ec8ef-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span><span class="sxs-lookup"><span data-stu-id="ec8ef-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="ec8ef-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span><span class="sxs-lookup"><span data-stu-id="ec8ef-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ec8ef-109">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec8ef-109">.NET Framework Security</span></span>  
 <span data-ttu-id="ec8ef-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span><span class="sxs-lookup"><span data-stu-id="ec8ef-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="ec8ef-111">This reduces the chance of malicious code gaining access to the data.</span><span class="sxs-lookup"><span data-stu-id="ec8ef-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8ef-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec8ef-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="ec8ef-113">Variables objets</span><span class="sxs-lookup"><span data-stu-id="ec8ef-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ec8ef-114">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="ec8ef-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="ec8ef-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="ec8ef-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="ec8ef-116">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="ec8ef-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
