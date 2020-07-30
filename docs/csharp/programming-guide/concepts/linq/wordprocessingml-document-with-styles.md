---
title: Document WordprocessingML avec des styles
description: Cet exemple de document WordprocessingML contient des paragraphes mis en forme avec des styles. En savoir plus sur les parties de document qui se rapportent aux styles.
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: b799c1bee95d7d638e6a3210b4876ff036e088eb
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302202"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="329d9-104">Document WordprocessingML avec des styles</span><span class="sxs-lookup"><span data-stu-id="329d9-104">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="329d9-105">Les documents WordprocessingML plus complexes possèdent des paragraphes qui sont mis en forme à l'aide de styles.</span><span class="sxs-lookup"><span data-stu-id="329d9-105">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="329d9-106">Quelques remarques relatives à la composition des documents WordprocessingML sont utiles.</span><span class="sxs-lookup"><span data-stu-id="329d9-106">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="329d9-107">Les documents WordprocessingML sont stockés dans des packages.</span><span class="sxs-lookup"><span data-stu-id="329d9-107">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="329d9-108">Les packages sont composés de plusieurs parties (les parties ont une signification explicite lorsqu'ils sont utilisés dans le contexte des packages ; il s'agit de fichiers compressés ensemble de manière à constituer un package).</span><span class="sxs-lookup"><span data-stu-id="329d9-108">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="329d9-109">Si un document contient des paragraphes mis en forme avec des styles, il y a une partie de document qui contient des paragraphes auxquels des styles sont appliqués.</span><span class="sxs-lookup"><span data-stu-id="329d9-109">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="329d9-110">Il y a également une partie de style qui contient les styles auxquels il est fait référence dans le document.</span><span class="sxs-lookup"><span data-stu-id="329d9-110">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="329d9-111">Pour accéder à des packages, il est important d’utiliser les relations entre les parties plutôt qu’un chemin arbitraire.</span><span class="sxs-lookup"><span data-stu-id="329d9-111">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="329d9-112">Cet aspect dépasse la portée du didacticiel Manipulation de contenu dans un document WordprocessingML, mais les exemples de programmes fournis dans ce didacticiel illustrent l’approche correcte.</span><span class="sxs-lookup"><span data-stu-id="329d9-112">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="329d9-113">Un document qui utilise des styles</span><span class="sxs-lookup"><span data-stu-id="329d9-113">A Document that Uses Styles</span></span>  
 <span data-ttu-id="329d9-114">L’exemple WordML présenté dans la rubrique [Forme des documents WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) est très simple.</span><span class="sxs-lookup"><span data-stu-id="329d9-114">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="329d9-115">Le documents suivant est plus complexe : il possède des paragraphes qui sont mis en forme à l'aide de styles.</span><span class="sxs-lookup"><span data-stu-id="329d9-115">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="329d9-116">La manière la plus simple d’afficher le code XML qui compose un document Office Open XML consiste à exécuter l’[Exemple qui imprime des parties de document Office Open XML (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="329d9-116">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="329d9-117">Dans le document suivant, le premier paragraphe a le style `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="329d9-117">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="329d9-118">Plusieurs paragraphes ont le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="329d9-118">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="329d9-119">Certains autres paragraphes ont le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="329d9-119">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="329d9-120">En raison de cette complexité relative, il est plus intéressant d'analyser ce document avec LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="329d9-120">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="329d9-121">Dans les paragraphes ayant des styles autres que le style par défaut, les éléments de paragraphe ont un élément enfant nommé `w:pPr`, qui à son tour possède un élément enfant `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="329d9-121">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="329d9-122">Cet élément possède un attribut, `w:val`, qui contient le nom de style.</span><span class="sxs-lookup"><span data-stu-id="329d9-122">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="329d9-123">Si le paragraphe a le style par défaut, cela signifie que l'élément de paragraphe n'a pas d'élément enfant `w:p.Pr`.</span><span class="sxs-lookup"><span data-stu-id="329d9-123">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
