---
title: GetXmlNamespace, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353190"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="c5270-102">Opérateur GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5270-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="c5270-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="c5270-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5270-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5270-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="c5270-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c5270-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="c5270-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="c5270-106">Optional.</span></span> <span data-ttu-id="c5270-107">The string that identifies the XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="c5270-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="c5270-108">If supplied, this string must be a valid XML identifier.</span><span class="sxs-lookup"><span data-stu-id="c5270-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="c5270-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c5270-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="c5270-110">If no prefix is specified, the default namespace is returned.</span><span class="sxs-lookup"><span data-stu-id="c5270-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="c5270-111">If no default namespace is specified, the empty namespace is returned.</span><span class="sxs-lookup"><span data-stu-id="c5270-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5270-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5270-112">Return Value</span></span>  
 <span data-ttu-id="c5270-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="c5270-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5270-114">Notes</span><span class="sxs-lookup"><span data-stu-id="c5270-114">Remarks</span></span>  
 <span data-ttu-id="c5270-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="c5270-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="c5270-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="c5270-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="c5270-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span><span class="sxs-lookup"><span data-stu-id="c5270-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="c5270-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span><span class="sxs-lookup"><span data-stu-id="c5270-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5270-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5270-119">Example</span></span>  
 <span data-ttu-id="c5270-120">The following example imports `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="c5270-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c5270-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="c5270-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="c5270-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span><span class="sxs-lookup"><span data-stu-id="c5270-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="c5270-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span><span class="sxs-lookup"><span data-stu-id="c5270-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="c5270-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span><span class="sxs-lookup"><span data-stu-id="c5270-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="c5270-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5270-125">See also</span></span>

- [<span data-ttu-id="c5270-126">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="c5270-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="c5270-127">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5270-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
