---
title: Paramètres XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282530"
---
# <a name="xslt-parameters"></a><span data-ttu-id="ae92f-102">Paramètres XSLT</span><span class="sxs-lookup"><span data-stu-id="ae92f-102">XSLT Parameters</span></span>
<span data-ttu-id="ae92f-103">Des paramètres XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="ae92f-104">Un nom qualifié et un URI d'espace de noms sont associés à l'objet de paramètre à ce stade.</span><span class="sxs-lookup"><span data-stu-id="ae92f-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="ae92f-105">Pour utiliser un paramètre XSLT</span><span class="sxs-lookup"><span data-stu-id="ae92f-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="ae92f-106">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez le paramètre à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="ae92f-107">Appelez le paramètre à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="ae92f-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="ae92f-108">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="ae92f-109">Types de paramètres</span><span class="sxs-lookup"><span data-stu-id="ae92f-109">Parameter Types</span></span>  
 <span data-ttu-id="ae92f-110">L'objet de paramètre doit correspondre à un type W3C.</span><span class="sxs-lookup"><span data-stu-id="ae92f-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="ae92f-111">Le tableau suivant illustre les types W3C correspondants, les classes Microsoft .NET Framework équivalentes (type) et précise si le type W3C est un type XPath ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="ae92f-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="ae92f-112">Type W3C</span><span class="sxs-lookup"><span data-stu-id="ae92f-112">W3C type</span></span>|<span data-ttu-id="ae92f-113">Équivalent de classe .NET (type)</span><span class="sxs-lookup"><span data-stu-id="ae92f-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="ae92f-114">Type XPath ou XSLT</span><span class="sxs-lookup"><span data-stu-id="ae92f-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="ae92f-115">XPath</span><span class="sxs-lookup"><span data-stu-id="ae92f-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="ae92f-116">XPath</span><span class="sxs-lookup"><span data-stu-id="ae92f-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="ae92f-117">XPath</span><span class="sxs-lookup"><span data-stu-id="ae92f-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="ae92f-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="ae92f-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="ae92f-119">XPath</span><span class="sxs-lookup"><span data-stu-id="ae92f-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="ae92f-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="ae92f-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="ae92f-121">XPath</span><span class="sxs-lookup"><span data-stu-id="ae92f-121">XPath</span></span>|  
  
 <span data-ttu-id="ae92f-122">\*Cela équivaut à une collection de nœuds contenant un seul nœud.</span><span class="sxs-lookup"><span data-stu-id="ae92f-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="ae92f-123">Si l'objet de paramètre n'est pas l'une des classes ci-dessus, il est converti selon les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="ae92f-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="ae92f-124">Les types CLR numériques sont convertis en objet <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="ae92f-125">Le type <xref:System.DateTime> est converti en <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="ae92f-126">Les types <xref:System.Xml.XPath.IXPathNavigable> sont convertis en <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ae92f-127">**XPathNavigator[]** est converti en objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="ae92f-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="ae92f-128">Tous les autres types provoquent une erreur.</span><span class="sxs-lookup"><span data-stu-id="ae92f-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae92f-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae92f-129">Example</span></span>  
 <span data-ttu-id="ae92f-130">L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> pour créer un paramètre destiné à contenir une date de remise calculée.</span><span class="sxs-lookup"><span data-stu-id="ae92f-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="ae92f-131">La date de la remise correspond à 20 jours à partir de la date de la commande.</span><span class="sxs-lookup"><span data-stu-id="ae92f-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="ae92f-132">Entrée</span><span class="sxs-lookup"><span data-stu-id="ae92f-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="ae92f-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="ae92f-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="ae92f-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="ae92f-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="ae92f-135">Output</span><span class="sxs-lookup"><span data-stu-id="ae92f-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae92f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae92f-136">See also</span></span>

- [<span data-ttu-id="ae92f-137">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="ae92f-137">XSLT Transformations</span></span>](xslt-transformations.md)
