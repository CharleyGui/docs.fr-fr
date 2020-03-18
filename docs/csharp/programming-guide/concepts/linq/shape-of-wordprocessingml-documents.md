---
title: Forme des documents WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732673"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="9412d-102">Forme des documents WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="9412d-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="9412d-103">Cette rubrique présente la forme XML d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9412d-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="9412d-104">Formats Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="9412d-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="9412d-105">Le format de fichier natif pour la version 2007 de Microsoft Office System est le format XML ouvert Microsoft Office (communément appelé Open XML).</span><span class="sxs-lookup"><span data-stu-id="9412d-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="9412d-106">Open XML est un format XML compatible avec la norme ECMA et actuellement soumis à un processus de normalisation ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="9412d-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="9412d-107">Le langage de balisage pour les fichiers de traitement de texte dans Open XML se nomme WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9412d-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="9412d-108">Ce didacticiel utilise des fichiers sources WordprocessingML comme entrée pour les exemples.</span><span class="sxs-lookup"><span data-stu-id="9412d-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="9412d-109">Si vous utilisez Microsoft Office 2003, vous pouvez enregistrer des documents au format Office Open XML si vous avez installé le Module de compatibilité Microsoft Office pour formats de fichiers Word, Excel et PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="9412d-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="9412d-110">Forme des documents WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="9412d-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="9412d-111">La première chose à comprendre est la forme des documents WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9412d-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="9412d-112">Un document WordprocessingML contient un élément de corps (nommé `w:body`) qui contient les paragraphes du document.</span><span class="sxs-lookup"><span data-stu-id="9412d-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="9412d-113">Chaque paragraphe contient une ou plusieurs exécutions de texte (nommées `w:r`).</span><span class="sxs-lookup"><span data-stu-id="9412d-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="9412d-114">Chaque exécution de texte contient un ou plusieurs segments de texte (nommés `w:t`).</span><span class="sxs-lookup"><span data-stu-id="9412d-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="9412d-115">Voici un document WordprocessingML très simple :</span><span class="sxs-lookup"><span data-stu-id="9412d-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
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
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="9412d-116">Ce document contient deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="9412d-116">This document contains two paragraphs.</span></span> <span data-ttu-id="9412d-117">Tous deux contiennent une seule exécution de texte et chaque exécution de texte contient un seul segment de texte.</span><span class="sxs-lookup"><span data-stu-id="9412d-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="9412d-118">Le moyen le plus simple d'afficher le contenu d'un fichier WordprocessingML au format XML consiste à en créer un à l'aide de Microsoft Word, de l'enregistrer, puis d'exécuter le programme suivant qui imprime le code XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="9412d-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="9412d-119">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="9412d-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="9412d-120">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9412d-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="9412d-121">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="9412d-121">External resources</span></span>

- [<span data-ttu-id="9412d-122">Présentation des formats de fichier Open XML Microsoft Office (2007)</span><span class="sxs-lookup"><span data-stu-id="9412d-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="9412d-123">Vue d’ensemble de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="9412d-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="9412d-124">Anatomie d’un fichier WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="9412d-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="9412d-125">Introduction à WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="9412d-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="9412d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9412d-126">See also</span></span>

- [<span data-ttu-id="9412d-127">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="9412d-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
