---
title: "Comment : référencer l'instance actuelle d'un objet"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410423"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="0eb21-102">Comment : référencer l'instance actuelle d'un objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0eb21-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="0eb21-103">L' *instance actuelle* d’un objet est l’instance dans laquelle le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0eb21-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="0eb21-104">Vous utilisez le `Me` mot clé pour faire référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="0eb21-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="0eb21-105">Pour faire référence à l’instance actuelle</span><span class="sxs-lookup"><span data-stu-id="0eb21-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="0eb21-106">Utilisez le `Me` mot clé dans lequel vous utiliseriez normalement le nom d’une variable objet.</span><span class="sxs-lookup"><span data-stu-id="0eb21-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="0eb21-107">Bien que `Me` se comporte comme une variable objet, vous ne pouvez pas le déclarer ou lui affecter n’importe quoi.</span><span class="sxs-lookup"><span data-stu-id="0eb21-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="0eb21-108">`Me`fait toujours référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="0eb21-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb21-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eb21-109">See also</span></span>

- [<span data-ttu-id="0eb21-110">Variables objets</span><span class="sxs-lookup"><span data-stu-id="0eb21-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="0eb21-111">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="0eb21-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="0eb21-112">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="0eb21-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
