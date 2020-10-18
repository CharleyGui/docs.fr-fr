---
title: L'attribut '<attributename>' ne peut pas être appliqué plusieurs fois
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162659"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="4fdc1-102">BC30663 : l’attribut' \<attributename> 'ne peut pas être appliqué plusieurs fois</span><span class="sxs-lookup"><span data-stu-id="4fdc1-102">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="4fdc1-103">L’attribut ne peut être appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="4fdc1-103">The attribute can only be applied once.</span></span> <span data-ttu-id="4fdc1-104">L' `AttributeUsage` attribut détermine si un attribut peut être appliqué plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4fdc1-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="4fdc1-105">**ID d’erreur :** BC30663</span><span class="sxs-lookup"><span data-stu-id="4fdc1-105">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4fdc1-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4fdc1-106">To correct this error</span></span>

1. <span data-ttu-id="4fdc1-107">Assurez-vous que l’attribut n’est appliqué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="4fdc1-107">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="4fdc1-108">Si vous utilisez des attributs personnalisés que vous avez développés, pensez `AttributeUsage` à modifier leur attribut pour permettre l’utilisation de plusieurs attributs, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4fdc1-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="4fdc1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fdc1-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="4fdc1-110">Création d'attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="4fdc1-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="4fdc1-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="4fdc1-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
