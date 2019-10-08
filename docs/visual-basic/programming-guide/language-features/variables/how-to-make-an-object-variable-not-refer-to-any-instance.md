---
title: 'Procédure : Faire en sorte qu’une variable objet ne fasse pas référence à une instance (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004917"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="d40a4-102">Procédure : Faire en sorte qu’une variable objet ne fasse pas référence à une instance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d40a4-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="d40a4-103">Vous pouvez dissocier une variable objet d’une instance d’objet en lui affectant la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d40a4-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="d40a4-104">Pour dissocier une variable objet d’une instance d’objet</span><span class="sxs-lookup"><span data-stu-id="d40a4-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="d40a4-105">Affectez à la variable la valeur `Nothing` dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="d40a4-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="d40a4-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d40a4-106">Robust Programming</span></span>  
 <span data-ttu-id="d40a4-107">Si votre code tente d’accéder à un membre d’une variable objet qui a été définie sur `Nothing`, une <xref:System.NullReferenceException> se produit.</span><span class="sxs-lookup"><span data-stu-id="d40a4-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="d40a4-108">Si vous affectez à une variable objet la valeur `Nothing` fréquemment, ou si la variable n’est pas initialisée, il est judicieux de placer les accès aux membres dans un bloc `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="d40a4-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d40a4-109">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d40a4-109">.NET Framework Security</span></span>  
 <span data-ttu-id="d40a4-110">Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez définir la variable sur `Nothing` lorsque vous n’êtes pas activement confronté à l’un de ces objets.</span><span class="sxs-lookup"><span data-stu-id="d40a4-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="d40a4-111">Cela réduit le risque que du code malveillant ait accès aux données.</span><span class="sxs-lookup"><span data-stu-id="d40a4-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40a4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d40a4-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="d40a4-113">Variables objets</span><span class="sxs-lookup"><span data-stu-id="d40a4-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="d40a4-114">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="d40a4-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="d40a4-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="d40a4-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="d40a4-116">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="d40a4-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
