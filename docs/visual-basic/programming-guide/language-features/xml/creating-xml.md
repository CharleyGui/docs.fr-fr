---
title: Création de code XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 0777b428d651c09d4bfb9789ab7b2ac8e74cc32e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410281"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="8b7a8-102">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b7a8-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="8b7a8-103">Visual Basic vous permet d’utiliser des *littéraux XML* directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="8b7a8-104">La syntaxe de littéral XML représente des [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets, et elle est semblable à la syntaxe xml 1,0.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="8b7a8-105">Il est ainsi plus facile de créer des éléments, des documents et des fragments XML par programme, car votre code a la même structure que le XML final.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b7a8-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8b7a8-106">In This Section</span></span>  
  
|<span data-ttu-id="8b7a8-107">Terme</span><span class="sxs-lookup"><span data-stu-id="8b7a8-107">Term</span></span>|<span data-ttu-id="8b7a8-108">Définition</span><span class="sxs-lookup"><span data-stu-id="8b7a8-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="8b7a8-109">Vue d'ensemble des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-109">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="8b7a8-110">Introduction aux littéraux XML et à leur relation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8b7a8-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="8b7a8-111">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-111">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="8b7a8-112">Décrit comment utiliser des expressions incorporées dans des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="8b7a8-113">Comment : créer des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-113">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="8b7a8-114">Décrit comment créer un élément XML dans le code à l’aide d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="8b7a8-115">Espaces blancs dans les littéraux XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-115">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="8b7a8-116">Décrit comment Visual Basic traite les espaces blancs dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="8b7a8-117">Littéraux XML et spécification XML 1.0</span><span class="sxs-lookup"><span data-stu-id="8b7a8-117">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="8b7a8-118">Décrit comment la syntaxe de littéral XML dans Visual Basic est associée à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="8b7a8-119">Guide pratique : incorporer des expressions dans des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-119">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="8b7a8-120">Explique comment utiliser des expressions incorporées dans des littéraux XML pour créer du contenu au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="8b7a8-121">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="8b7a8-121">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="8b7a8-122">Décrit les instructions pour nommer des éléments et des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="8b7a8-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b7a8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b7a8-123">See also</span></span>

- [<span data-ttu-id="8b7a8-124">XML</span><span class="sxs-lookup"><span data-stu-id="8b7a8-124">XML</span></span>](index.md)
