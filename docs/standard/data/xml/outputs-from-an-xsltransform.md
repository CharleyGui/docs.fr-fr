---
title: Sorties à partir de XslTransform
ms.date: 03/30/2017
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: ebe276a9627a36f1248f0043af6c82e76fe7fd78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691368"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="5e0fb-102">Sorties à partir de XslTransform</span><span class="sxs-lookup"><span data-stu-id="5e0fb-102">Outputs from an XslTransform</span></span>

<span data-ttu-id="5e0fb-103">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e0fb-104">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="5e0fb-105">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5e0fb-106">Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="5e0fb-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="5e0fb-107">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="5e0fb-108">Le tableau suivant décrit ce qui se produit lorsqu'un type de sortie est déclaré par la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> conjointement à l'utilisation d'une instruction `<xsl:output>` :</span><span class="sxs-lookup"><span data-stu-id="5e0fb-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="5e0fb-109">Attribut \<xsl:output method = ></span><span class="sxs-lookup"><span data-stu-id="5e0fb-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="5e0fb-110">Format de résultat</span><span class="sxs-lookup"><span data-stu-id="5e0fb-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="5e0fb-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="5e0fb-111">method="xml"</span></span>|<span data-ttu-id="5e0fb-112">XML</span><span class="sxs-lookup"><span data-stu-id="5e0fb-112">XML</span></span>|  
|<span data-ttu-id="5e0fb-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="5e0fb-113">method="html"</span></span>|<span data-ttu-id="5e0fb-114">HTML</span><span class="sxs-lookup"><span data-stu-id="5e0fb-114">HTML</span></span>|  
|<span data-ttu-id="5e0fb-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="5e0fb-115">method="text"</span></span>|<span data-ttu-id="5e0fb-116">Texte</span><span class="sxs-lookup"><span data-stu-id="5e0fb-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="5e0fb-117">Remarque : l'instruction `<xsl:output>` est ignorée lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="5e0fb-118">Les attributs suivants sont pris en charge lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="5e0fb-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="5e0fb-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="5e0fb-119">encoding\*</span></span>  
  
- <span data-ttu-id="5e0fb-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="5e0fb-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="5e0fb-121">autonomes</span><span class="sxs-lookup"><span data-stu-id="5e0fb-121">standalone</span></span>  
  
- <span data-ttu-id="5e0fb-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="5e0fb-122">doctype-public</span></span>  
  
- <span data-ttu-id="5e0fb-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="5e0fb-123">doctype-system</span></span>  
  
- <span data-ttu-id="5e0fb-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="5e0fb-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="5e0fb-125">indent</span><span class="sxs-lookup"><span data-stu-id="5e0fb-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5e0fb-126">\*L’attribut encoding est ignoré quand la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> envoie sa sortie à un <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="5e0fb-127">La propriété encoding sur l'objet <xref:System.IO.TextWriter> est utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="5e0fb-128">Les attributs suivants sont ignorés lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="5e0fb-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="5e0fb-129">version : la version est toujours 1.0 ;</span><span class="sxs-lookup"><span data-stu-id="5e0fb-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="5e0fb-130">media-type : le type de média.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="5e0fb-131">Échappement de caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="5e0fb-131">Escaping Special Characters</span></span>  

 <span data-ttu-id="5e0fb-132">La balise `<xsl:text disable-output-escaping>` est utilisée pour indiquer si des caractères spéciaux doivent ou non être placés dans une séquence d'échappement dans un formulaire XML (par exemple, en substituant `<&lt>` au symbole `"<"`) ou laissés tels quels.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="5e0fb-133">L'attribut `disable-output-escaping` est ignoré lors de la transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> et n'a pas d'effet sur les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0fb-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e0fb-134">See also</span></span>

- [<span data-ttu-id="5e0fb-135">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="5e0fb-135">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
