---
title: Les propriétés d'axe XML ne prennent pas en charge la liaison tardive
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: caa0934ba4ab7e80ae9598b4772e5e49c1ec7f41
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875016"
---
# <a name="xml-axis-properties-do-not-support-late-binding"></a><span data-ttu-id="1dc85-102">Les propriétés d'axe XML ne prennent pas en charge la liaison tardive</span><span class="sxs-lookup"><span data-stu-id="1dc85-102">XML axis properties do not support late binding</span></span>

<span data-ttu-id="1dc85-103">Une propriété d’axe XML a été référencée pour un objet non typé.</span><span class="sxs-lookup"><span data-stu-id="1dc85-103">An XML axis property has been referenced for an untyped object.</span></span>  
  
 <span data-ttu-id="1dc85-104">**ID d’erreur :** BC31168</span><span class="sxs-lookup"><span data-stu-id="1dc85-104">**Error ID:** BC31168</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1dc85-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1dc85-105">To correct this error</span></span>  
  
- <span data-ttu-id="1dc85-106">Assurez-vous que l’objet est un objet de type fort <xref:System.Xml.Linq.XElement> avant de référencer la propriété d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="1dc85-106">Ensure that the object is a strong-typed <xref:System.Xml.Linq.XElement> object before referencing the XML axis property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc85-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dc85-107">See also</span></span>

- [<span data-ttu-id="1dc85-108">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="1dc85-108">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="1dc85-109">XML</span><span class="sxs-lookup"><span data-stu-id="1dc85-109">XML</span></span>](../../programming-guide/language-features/xml/index.md)
