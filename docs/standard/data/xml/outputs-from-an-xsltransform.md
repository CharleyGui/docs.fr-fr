---
title: Sorties à partir de XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 93cbf7807630a605e17e7f513055c052aad0d08e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159635"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="52596-102">Sorties à partir de XslTransform</span><span class="sxs-lookup"><span data-stu-id="52596-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="52596-103">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="52596-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52596-104">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="52596-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="52596-105">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="52596-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="52596-106">Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="52596-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="52596-107">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="52596-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="52596-108">Le tableau suivant décrit ce qui se produit lorsqu'un type de sortie est déclaré par la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> conjointement à l'utilisation d'une instruction `<xsl:output>` :</span><span class="sxs-lookup"><span data-stu-id="52596-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="52596-109">méthode \<xsl:output = > attribut</span><span class="sxs-lookup"><span data-stu-id="52596-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="52596-110">Format de résultat</span><span class="sxs-lookup"><span data-stu-id="52596-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="52596-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="52596-111">method="xml"</span></span>|<span data-ttu-id="52596-112">XML</span><span class="sxs-lookup"><span data-stu-id="52596-112">XML</span></span>|  
|<span data-ttu-id="52596-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="52596-113">method="html"</span></span>|<span data-ttu-id="52596-114">HTML</span><span class="sxs-lookup"><span data-stu-id="52596-114">HTML</span></span>|  
|<span data-ttu-id="52596-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="52596-115">method="text"</span></span>|<span data-ttu-id="52596-116">Texte</span><span class="sxs-lookup"><span data-stu-id="52596-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="52596-117">Remarque : l'instruction `<xsl:output>` est ignorée lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="52596-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="52596-118">Les attributs suivants sont pris en charge lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="52596-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="52596-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="52596-119">encoding\*</span></span>  
  
- <span data-ttu-id="52596-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="52596-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="52596-121">standalone</span><span class="sxs-lookup"><span data-stu-id="52596-121">standalone</span></span>  
  
- <span data-ttu-id="52596-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="52596-122">doctype-public</span></span>  
  
- <span data-ttu-id="52596-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="52596-123">doctype-system</span></span>  
  
- <span data-ttu-id="52596-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="52596-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="52596-125">indent</span><span class="sxs-lookup"><span data-stu-id="52596-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="52596-126">\*L’attribut encoding est ignoré quand la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> envoie sa sortie à un <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="52596-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="52596-127">La propriété encoding sur l'objet <xref:System.IO.TextWriter> est utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="52596-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="52596-128">Les attributs suivants sont ignorés lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="52596-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="52596-129">version : la version est toujours 1.0 ;</span><span class="sxs-lookup"><span data-stu-id="52596-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="52596-130">media-type : le type de média.</span><span class="sxs-lookup"><span data-stu-id="52596-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="52596-131">Échappement de caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="52596-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="52596-132">La balise `<xsl:text disable-output-escaping>` est utilisée pour indiquer si des caractères spéciaux doivent ou non être placés dans une séquence d'échappement dans un formulaire XML (par exemple, en substituant `<&lt>` au symbole `"<"`) ou laissés tels quels.</span><span class="sxs-lookup"><span data-stu-id="52596-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="52596-133">L'attribut `disable-output-escaping` est ignoré lors de la transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> et n'a pas d'effet sur les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="52596-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52596-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52596-134">See also</span></span>

- [<span data-ttu-id="52596-135">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="52596-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
