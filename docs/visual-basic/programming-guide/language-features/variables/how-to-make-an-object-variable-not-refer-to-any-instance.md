---
title: "Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance"
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410449"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="fdd58-102">Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdd58-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="fdd58-103">Vous pouvez dissocier une variable objet d’une instance d’objet en lui affectant la valeur [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="fdd58-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="fdd58-104">Pour dissocier une variable objet d’une instance d’objet</span><span class="sxs-lookup"><span data-stu-id="fdd58-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="fdd58-105">Affectez à la variable la valeur `Nothing` dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="fdd58-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="fdd58-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fdd58-106">Robust Programming</span></span>  
 <span data-ttu-id="fdd58-107">Si votre code tente d’accéder à un membre d’une variable objet qui a été définie sur `Nothing` , une <xref:System.NullReferenceException> se produit.</span><span class="sxs-lookup"><span data-stu-id="fdd58-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="fdd58-108">Si vous définissez une variable objet sur `Nothing` fréquemment, ou s’il est possible que la variable ne soit pas initialisée, il est judicieux de délimiter les accès aux membres dans un `Try...Catch...Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="fdd58-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fdd58-109">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fdd58-109">.NET Framework Security</span></span>  
 <span data-ttu-id="fdd58-110">Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez affecter à la variable la valeur `Nothing` lorsque vous ne traitez pas activement l’un de ces objets.</span><span class="sxs-lookup"><span data-stu-id="fdd58-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="fdd58-111">Cela réduit le risque que du code malveillant ait accès aux données.</span><span class="sxs-lookup"><span data-stu-id="fdd58-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd58-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdd58-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="fdd58-113">Variables objets</span><span class="sxs-lookup"><span data-stu-id="fdd58-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="fdd58-114">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="fdd58-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="fdd58-115">Résultat</span><span class="sxs-lookup"><span data-stu-id="fdd58-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="fdd58-116">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="fdd58-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
