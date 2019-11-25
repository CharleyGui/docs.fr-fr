---
title: Nom des attributs et des éléments XML déclarés
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335989"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="ebc9a-102">Nom des attributs et des éléments XML déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebc9a-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="ebc9a-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="ebc9a-104">In an XML literal, you can specify a local name or a qualified name.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="ebc9a-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="ebc9a-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ebc9a-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ebc9a-107">Règles</span><span class="sxs-lookup"><span data-stu-id="ebc9a-107">Rules</span></span>  
 <span data-ttu-id="ebc9a-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="ebc9a-109">It can begin with a namespace.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-109">It can begin with a namespace.</span></span> <span data-ttu-id="ebc9a-110">It must begin with an alphabetical character or an underscore (`_`).</span><span class="sxs-lookup"><span data-stu-id="ebc9a-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="ebc9a-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span><span class="sxs-lookup"><span data-stu-id="ebc9a-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="ebc9a-112">It must not be more than 1,024 characters long.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="ebc9a-113">Colons that appear in names indicate namespace demarcation.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="ebc9a-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="ebc9a-115">In addition, you should adhere to the following guideline.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="ebc9a-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="ebc9a-117">Therefore, do not use those names for your element and attribute names.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="ebc9a-118">Name Length Guidelines</span><span class="sxs-lookup"><span data-stu-id="ebc9a-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="ebc9a-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="ebc9a-120">This improves the readability of your code and reduces line length and source-file size.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="ebc9a-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="ebc9a-122">This is important for the readability of your code.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-122">This is important for the readability of your code.</span></span> <span data-ttu-id="ebc9a-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="ebc9a-124">Case Sensitivity in Names</span><span class="sxs-lookup"><span data-stu-id="ebc9a-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="ebc9a-125">XML element names are case sensitive.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-125">XML element names are case sensitive.</span></span> <span data-ttu-id="ebc9a-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="ebc9a-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="ebc9a-128">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="ebc9a-128">XML Namespaces</span></span>  
 <span data-ttu-id="ebc9a-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span><span class="sxs-lookup"><span data-stu-id="ebc9a-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="ebc9a-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ebc9a-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc9a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebc9a-131">See also</span></span>

- [<span data-ttu-id="ebc9a-132">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebc9a-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ebc9a-133">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="ebc9a-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
