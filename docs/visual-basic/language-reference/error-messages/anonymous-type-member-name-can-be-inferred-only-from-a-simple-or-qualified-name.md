---
title: Le nom du membre de type anonyme ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 38f669fe183ac79ebed6e5a122bc70aedc9bb753
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701224"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="608b5-102">Le nom du membre de type anonyme ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument</span><span class="sxs-lookup"><span data-stu-id="608b5-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="608b5-103">Vous ne pouvez pas déduire un nom de membre de type anonyme à partir d’une expression complexe.</span><span class="sxs-lookup"><span data-stu-id="608b5-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="608b5-104">Pour plus d’informations sur les sources à partir desquelles les types anonymes peuvent et ne peuvent pas déduire les noms et les types de membres, consultez [How pour : Déduire les types et les noms de propriétés dans des déclarations de type anonyme @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="608b5-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="608b5-105">**ID d’erreur :** BC36556</span><span class="sxs-lookup"><span data-stu-id="608b5-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="608b5-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="608b5-106">To correct this error</span></span>  
  
- <span data-ttu-id="608b5-107">Assignez l’expression à un nom de membre, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="608b5-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```vb  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="608b5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="608b5-108">See also</span></span>

- [<span data-ttu-id="608b5-109">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="608b5-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- <span data-ttu-id="608b5-110">[Guide pratique pour Déduire les types et les noms de propriétés dans des déclarations de type anonyme @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="608b5-110">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>
