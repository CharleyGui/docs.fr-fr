---
title: Forme XML des documents WordprocessingML-LINQ to XML
description: En savoir plus sur la forme XML d’un document WordprocessingML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 0c6ed589556eb35a5741739c1f87e1e175476c89
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553212"
---
# <a name="the-xml-shape-of-wordprocessingml-documents-linq-to-xml"></a><span data-ttu-id="9a89b-103">Forme XML des documents WordprocessingML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9a89b-103">The XML shape of WordprocessingML documents (LINQ to XML)</span></span>

<span data-ttu-id="9a89b-104">Cet article présente la forme XML d’un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9a89b-104">This article introduces the XML shape of a WordprocessingML document.</span></span>

## <a name="microsoft-office-formats"></a><span data-ttu-id="9a89b-105">Formats de Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="9a89b-105">Microsoft Office formats</span></span>

<span data-ttu-id="9a89b-106">Le format de fichier natif pour la version 2007 de Microsoft Office System est le format XML ouvert Microsoft Office (communément appelé Open XML).</span><span class="sxs-lookup"><span data-stu-id="9a89b-106">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="9a89b-107">Open XML est un format basé sur XML qui est une norme ECMA et qui passe actuellement par le processus de normalisation ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="9a89b-107">Open XML is an XML-based format that's an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="9a89b-108">Le langage de balisage pour les fichiers de traitement de texte dans Open XML se nomme WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9a89b-108">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="9a89b-109">Ce didacticiel utilise des fichiers sources WordprocessingML comme entrée pour les exemples.</span><span class="sxs-lookup"><span data-stu-id="9a89b-109">This tutorial uses WordprocessingML source files as input for the examples.</span></span>

<span data-ttu-id="9a89b-110">Si vous utilisez Microsoft Office 2003, vous pouvez enregistrer des documents au format Office Open XML si vous avez installé le pack d’Microsoft Office compatibilité pour les formats de fichiers Word, Excel et PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="9a89b-110">If you're using Microsoft Office 2003, you can save documents in the Office Open XML format if you've installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="9a89b-111">Forme des documents WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="9a89b-111">The shape of WordprocessingML documents</span></span>

<span data-ttu-id="9a89b-112">La première chose à comprendre est la forme XML des documents WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="9a89b-112">The first thing to understand is the XML shape of WordprocessingML documents.</span></span> <span data-ttu-id="9a89b-113">Un document WordprocessingML contient un élément de corps (nommé `w:body`) qui contient les paragraphes du document.</span><span class="sxs-lookup"><span data-stu-id="9a89b-113">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="9a89b-114">Chaque paragraphe contient une ou plusieurs exécutions de texte (nommées `w:r`).</span><span class="sxs-lookup"><span data-stu-id="9a89b-114">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="9a89b-115">Chaque exécution de texte contient un ou plusieurs segments de texte (nommés `w:t`).</span><span class="sxs-lookup"><span data-stu-id="9a89b-115">Each text run contains one or more text pieces (named `w:t`).</span></span>

<span data-ttu-id="9a89b-116">Voici un document WordprocessingML très simple :</span><span class="sxs-lookup"><span data-stu-id="9a89b-116">The following is a very simple WordprocessingML document:</span></span>

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

<span data-ttu-id="9a89b-117">Ce document contient deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="9a89b-117">This document contains two paragraphs.</span></span> <span data-ttu-id="9a89b-118">Tous deux contiennent une seule exécution de texte et chaque exécution de texte contient un seul segment de texte.</span><span class="sxs-lookup"><span data-stu-id="9a89b-118">They both contain a single text run, and each text run contains a single text piece.</span></span>

<span data-ttu-id="9a89b-119">Le moyen le plus simple d'afficher le contenu d'un fichier WordprocessingML au format XML consiste à en créer un à l'aide de Microsoft Word, de l'enregistrer, puis d'exécuter le programme suivant qui imprime le code XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="9a89b-119">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>

<span data-ttu-id="9a89b-120">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="9a89b-120">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="9a89b-121">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a89b-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Sub Main()
        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"

        Using wdPackage As Package = _
          Package.Open("SampleDoc.docx", _
                       FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage _
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _
                            New Uri("/", UriKind.Relative), _
                            docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Get the officeDocument part from the package.
                ' Load the XML in the part into an XDocument instance.
                Dim xDoc As XDocument = _
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))
                Console.WriteLine(xDoc.Root)
            End If
        End Using
    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="9a89b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a89b-122">See also</span></span>

- <span data-ttu-id="9a89b-123">[Présentation des formats de fichier Open XML Microsoft Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="9a89b-123">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>
- <span data-ttu-id="9a89b-124">[Vue d’ensemble de WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="9a89b-124">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>
- [<span data-ttu-id="9a89b-125">Anatomie d’un fichier WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="9a89b-125">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="9a89b-126">Introduction à WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="9a89b-126">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)
