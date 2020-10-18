---
title: Les propriétés d'axe XML ne prennent pas en charge la liaison tardive
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: 9eef245d6f83770ce26bc9e753711543241d57fb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163283"
---
# <a name="bc31168-xml-axis-properties-do-not-support-late-binding"></a><span data-ttu-id="9f37e-102">BC31168 : les propriétés d’axe XML ne prennent pas en charge la liaison tardive</span><span class="sxs-lookup"><span data-stu-id="9f37e-102">BC31168: XML axis properties do not support late binding</span></span>

<span data-ttu-id="9f37e-103">Une propriété d’axe XML a été référencée pour un objet non typé.</span><span class="sxs-lookup"><span data-stu-id="9f37e-103">An XML axis property has been referenced for an untyped object.</span></span>

 <span data-ttu-id="9f37e-104">**ID d’erreur :** BC31168</span><span class="sxs-lookup"><span data-stu-id="9f37e-104">**Error ID:** BC31168</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9f37e-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9f37e-105">To correct this error</span></span>

- <span data-ttu-id="9f37e-106">Assurez-vous que l’objet est un objet de type fort <xref:System.Xml.Linq.XElement> avant de référencer la propriété d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="9f37e-106">Ensure that the object is a strong-typed <xref:System.Xml.Linq.XElement> object before referencing the XML axis property.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f37e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f37e-107">See also</span></span>

- [<span data-ttu-id="9f37e-108">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="9f37e-108">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="9f37e-109">XML</span><span class="sxs-lookup"><span data-stu-id="9f37e-109">XML</span></span>](../../programming-guide/language-features/xml/index.md)
