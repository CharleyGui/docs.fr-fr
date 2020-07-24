---
title: Exemple qui imprime des parties de document Office Open XML (C#)
description: Découvrez comment ouvrir un document Office Open XML et y accéder à l’aide de LINQ en C#. Cet exemple imprime la partie document et la partie de style d’un document.
ms.date: 07/20/2015
ms.assetid: 6cd37055-89b4-42e8-bf27-5a29717e35f3
ms.openlocfilehash: c5755ad8e8772195c056b0c1c896c914b1a63a55
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103918"
---
# <a name="example-that-outputs-office-open-xml-document-parts-c"></a><span data-ttu-id="271ce-104">Exemple qui imprime des parties de document Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="271ce-104">Example that Outputs Office Open XML Document Parts (C#)</span></span>
<span data-ttu-id="271ce-105">Cette rubrique montre comment ouvrir un document Office Open XML et accéder à ses parties.</span><span class="sxs-lookup"><span data-stu-id="271ce-105">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="271ce-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="271ce-106">Example</span></span>  
 <span data-ttu-id="271ce-107">L'exemple suivant ouvre un document Office Open XML et imprime la partie document et la partie de style sur la console.</span><span class="sxs-lookup"><span data-stu-id="271ce-107">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="271ce-108">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="271ce-108">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="271ce-109">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="271ce-109">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        XDocument xdoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri);  
        Console.WriteLine("==================================================================");  
        Console.WriteLine(xdoc.Root);  
        Console.WriteLine();  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            XDocument styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri);  
            Console.WriteLine("==================================================================");  
            Console.WriteLine(styleDoc.Root);  
            Console.WriteLine();  
        }  
    }  
}  
```  
