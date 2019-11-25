---
title: L'attribut '<attributename>' ne peut pas être appliqué plusieurs fois
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968227"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="3c49d-102">L’attribut'\<AttributeName > 'ne peut pas être appliqué plusieurs fois</span><span class="sxs-lookup"><span data-stu-id="3c49d-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="3c49d-103">L’attribut ne peut être appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3c49d-103">The attribute can only be applied once.</span></span> <span data-ttu-id="3c49d-104">L’attribut `AttributeUsage` détermine si un attribut peut être appliqué plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="3c49d-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="3c49d-105">**ID d’erreur :** BC30663</span><span class="sxs-lookup"><span data-stu-id="3c49d-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c49d-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3c49d-106">To correct this error</span></span>  
  
1. <span data-ttu-id="3c49d-107">Assurez-vous que l’attribut n’est appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3c49d-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="3c49d-108">Si vous utilisez des attributs personnalisés que vous avez développés, pensez à modifier leur attribut `AttributeUsage` pour permettre l’utilisation de plusieurs attributs, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3c49d-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c49d-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c49d-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="3c49d-110">Création d’attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="3c49d-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="3c49d-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="3c49d-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
