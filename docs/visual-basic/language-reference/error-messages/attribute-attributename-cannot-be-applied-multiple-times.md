---
title: L'attribut '<attributename>' ne peut pas être appliqué plusieurs fois
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409957"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="01ffb-102">L'attribut '\<attributename>' ne peut pas être appliqué plusieurs fois</span><span class="sxs-lookup"><span data-stu-id="01ffb-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="01ffb-103">L’attribut ne peut être appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="01ffb-103">The attribute can only be applied once.</span></span> <span data-ttu-id="01ffb-104">L' `AttributeUsage` attribut détermine si un attribut peut être appliqué plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="01ffb-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="01ffb-105">**ID d’erreur :** BC30663</span><span class="sxs-lookup"><span data-stu-id="01ffb-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01ffb-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="01ffb-106">To correct this error</span></span>  
  
1. <span data-ttu-id="01ffb-107">Assurez-vous que l’attribut n’est appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="01ffb-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="01ffb-108">Si vous utilisez des attributs personnalisés que vous avez développés, pensez `AttributeUsage` à modifier leur attribut pour permettre l’utilisation de plusieurs attributs, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="01ffb-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01ffb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01ffb-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="01ffb-110">Création d'attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="01ffb-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="01ffb-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="01ffb-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
