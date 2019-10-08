---
title: 'Procédure : Faire référence à l’instance actuelle d’un objet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005655"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="c6f7b-102">Procédure : Faire référence à l’instance actuelle d’un objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6f7b-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="c6f7b-103">L' *instance actuelle* d’un objet est l’instance dans laquelle le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c6f7b-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="c6f7b-104">Vous utilisez le mot clé `Me` pour faire référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="c6f7b-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="c6f7b-105">Pour faire référence à l’instance actuelle</span><span class="sxs-lookup"><span data-stu-id="c6f7b-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="c6f7b-106">Utilisez le mot clé `Me` dans lequel vous utiliseriez normalement le nom d’une variable objet.</span><span class="sxs-lookup"><span data-stu-id="c6f7b-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="c6f7b-107">Bien que `Me` se comporte comme une variable objet, vous ne pouvez pas le déclarer ou lui affecter n’importe quoi.</span><span class="sxs-lookup"><span data-stu-id="c6f7b-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="c6f7b-108">`Me` fait toujours référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="c6f7b-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f7b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f7b-109">See also</span></span>

- [<span data-ttu-id="c6f7b-110">Variables objets</span><span class="sxs-lookup"><span data-stu-id="c6f7b-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c6f7b-111">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="c6f7b-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c6f7b-112">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="c6f7b-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
