---
title: Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870209"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="fdbb1-102">Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fdbb1-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="fdbb1-103">Les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé dans ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fdbb1-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="fdbb1-104">Pour utiliser les fonctionnalités XML, déplacez le code vers le code-behind.</span><span class="sxs-lookup"><span data-stu-id="fdbb1-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="fdbb1-105">Un littéral XML ou une propriété d’axe XML est défini dans du code incorporé ( `<%= =>` ) dans un fichier ASP.net.</span><span class="sxs-lookup"><span data-stu-id="fdbb1-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="fdbb1-106">**ID d’erreur :** BC31200</span><span class="sxs-lookup"><span data-stu-id="fdbb1-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fdbb1-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="fdbb1-107">To correct this error</span></span>  
  
- <span data-ttu-id="fdbb1-108">Déplacez le code qui comprend le littéral XML ou la propriété d’axe XML vers un fichier code-behind ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fdbb1-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbb1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdbb1-109">See also</span></span>

- [<span data-ttu-id="fdbb1-110">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="fdbb1-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="fdbb1-111">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="fdbb1-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="fdbb1-112">XML</span><span class="sxs-lookup"><span data-stu-id="fdbb1-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
