---
title: Paramètres XSLT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 64a62840594773270a658738120812c59b4896cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685212"
---
# <a name="xslt-parameters"></a><span data-ttu-id="6acff-102">Paramètres XSLT</span><span class="sxs-lookup"><span data-stu-id="6acff-102">XSLT Parameters</span></span>

<span data-ttu-id="6acff-103">Des paramètres XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="6acff-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="6acff-104">Un nom qualifié et un URI d'espace de noms sont associés à l'objet de paramètre à ce stade.</span><span class="sxs-lookup"><span data-stu-id="6acff-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="6acff-105">Pour utiliser un paramètre XSLT</span><span class="sxs-lookup"><span data-stu-id="6acff-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="6acff-106">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez le paramètre à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="6acff-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="6acff-107">Appelez le paramètre à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="6acff-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="6acff-108">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="6acff-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="6acff-109">Types de paramètres</span><span class="sxs-lookup"><span data-stu-id="6acff-109">Parameter Types</span></span>  

 <span data-ttu-id="6acff-110">L'objet de paramètre doit correspondre à un type W3C.</span><span class="sxs-lookup"><span data-stu-id="6acff-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="6acff-111">Le tableau suivant illustre les types W3C correspondants, les classes Microsoft .NET Framework équivalentes (type) et précise si le type W3C est un type XPath ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="6acff-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="6acff-112">Type W3C</span><span class="sxs-lookup"><span data-stu-id="6acff-112">W3C type</span></span>|<span data-ttu-id="6acff-113">Équivalent de classe .NET (type)</span><span class="sxs-lookup"><span data-stu-id="6acff-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="6acff-114">Type XPath ou XSLT</span><span class="sxs-lookup"><span data-stu-id="6acff-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="6acff-115">XPath</span><span class="sxs-lookup"><span data-stu-id="6acff-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="6acff-116">XPath</span><span class="sxs-lookup"><span data-stu-id="6acff-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="6acff-117">XPath</span><span class="sxs-lookup"><span data-stu-id="6acff-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="6acff-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="6acff-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="6acff-119">XPath</span><span class="sxs-lookup"><span data-stu-id="6acff-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="6acff-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="6acff-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="6acff-121">XPath</span><span class="sxs-lookup"><span data-stu-id="6acff-121">XPath</span></span>|  
  
 <span data-ttu-id="6acff-122">\*Cela équivaut à une collection de nœuds contenant un seul nœud.</span><span class="sxs-lookup"><span data-stu-id="6acff-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="6acff-123">Si l'objet de paramètre n'est pas l'une des classes ci-dessus, il est converti selon les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="6acff-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="6acff-124">Les types CLR numériques sont convertis en objet <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="6acff-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="6acff-125">Le type <xref:System.DateTime> est converti en <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6acff-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="6acff-126">Les types <xref:System.Xml.XPath.IXPathNavigable> sont convertis en <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6acff-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6acff-127">**XPathNavigator[]** est converti en objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="6acff-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="6acff-128">Tous les autres types provoquent une erreur.</span><span class="sxs-lookup"><span data-stu-id="6acff-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6acff-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="6acff-129">Example</span></span>  

 <span data-ttu-id="6acff-130">L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> pour créer un paramètre destiné à contenir une date de remise calculée.</span><span class="sxs-lookup"><span data-stu-id="6acff-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="6acff-131">La date de la remise correspond à 20 jours à partir de la date de la commande.</span><span class="sxs-lookup"><span data-stu-id="6acff-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="6acff-132">Entrée</span><span class="sxs-lookup"><span data-stu-id="6acff-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="6acff-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="6acff-133">order.xml</span></span>  

 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="6acff-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="6acff-134">discount.xsl</span></span>  

 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="6acff-135">Sortie</span><span class="sxs-lookup"><span data-stu-id="6acff-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6acff-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6acff-136">See also</span></span>

- [<span data-ttu-id="6acff-137">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="6acff-137">XSLT Transformations</span></span>](xslt-transformations.md)
