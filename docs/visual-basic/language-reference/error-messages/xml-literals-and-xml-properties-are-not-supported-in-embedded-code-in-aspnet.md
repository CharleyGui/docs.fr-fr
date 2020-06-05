---
title: Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406467"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="402c8-102">Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET</span><span class="sxs-lookup"><span data-stu-id="402c8-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="402c8-103">Les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé dans ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="402c8-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="402c8-104">Pour utiliser les fonctionnalités XML, déplacez le code vers le code-behind.</span><span class="sxs-lookup"><span data-stu-id="402c8-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="402c8-105">Un littéral XML ou une propriété d’axe XML est défini dans du code incorporé ( `<%= =>` ) dans un fichier ASP.net.</span><span class="sxs-lookup"><span data-stu-id="402c8-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="402c8-106">**ID d’erreur :** BC31200</span><span class="sxs-lookup"><span data-stu-id="402c8-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="402c8-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="402c8-107">To correct this error</span></span>  
  
- <span data-ttu-id="402c8-108">Déplacez le code qui comprend le littéral XML ou la propriété d’axe XML vers un fichier code-behind ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="402c8-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402c8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="402c8-109">See also</span></span>

- [<span data-ttu-id="402c8-110">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="402c8-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="402c8-111">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="402c8-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="402c8-112">XML</span><span class="sxs-lookup"><span data-stu-id="402c8-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
