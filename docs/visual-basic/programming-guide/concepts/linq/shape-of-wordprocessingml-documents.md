---
title: Forme des documents WordprocessingML
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: eb4acef2caa731d17e8daf1955d50f0d2585c175
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406805"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Forme des documents WordprocessingML (Visual Basic)
Cette rubrique présente la forme XML d'un document WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formats Microsoft Office  
 Le format de fichier natif pour la version 2007 de Microsoft Office System est le format XML ouvert Microsoft Office (communément appelé Open XML). Open XML est un format XML compatible avec la norme ECMA et actuellement soumis à un processus de normalisation ISO-IEC. Le langage de balisage pour les fichiers de traitement de texte dans Open XML se nomme WordprocessingML. Ce didacticiel utilise des fichiers sources WordprocessingML comme entrée pour les exemples.  
  
 Si vous utilisez Microsoft Office 2003, vous pouvez enregistrer des documents au format Office Open XML si vous avez installé le Module de compatibilité Microsoft Office pour formats de fichiers Word, Excel et PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Forme des documents WordprocessingML  
 La première chose à comprendre est la forme des documents WordprocessingML. Un document WordprocessingML contient un élément de corps (nommé `w:body`) qui contient les paragraphes du document. Chaque paragraphe contient une ou plusieurs exécutions de texte (nommées `w:r`). Chaque exécution de texte contient un ou plusieurs segments de texte (nommés `w:t`).  
  
 Voici un document WordprocessingML très simple :  
  
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
  
 Ce document contient deux paragraphes. Tous deux contiennent une seule exécution de texte et chaque exécution de texte contient un seul segment de texte.  
  
 Le moyen le plus simple d'afficher le contenu d'un fichier WordprocessingML au format XML consiste à en créer un à l'aide de Microsoft Word, de l'enregistrer, puis d'exécuter le programme suivant qui imprime le code XML sur la console.  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
## <a name="external-resources"></a>Ressources externes

- [Présentation des formats de fichier Open XML Microsoft Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))
- [Vue d’ensemble de WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))

## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
