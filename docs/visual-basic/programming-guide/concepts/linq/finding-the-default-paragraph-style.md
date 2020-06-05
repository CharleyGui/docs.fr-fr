---
title: Recherche du style de paragraphe par défaut
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: b70ae72c293d00c4f7b7a2601bfd20b85702b6d5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398075"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="e2ba3-102">Recherche du style de paragraphe par défaut (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ba3-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="e2ba3-103">La première tâche du didacticiel Manipulation d’informations dans un document WordprocessingML consiste à rechercher le style par défaut des paragraphes dans le document.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ba3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2ba3-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e2ba3-105">Description</span><span class="sxs-lookup"><span data-stu-id="e2ba3-105">Description</span></span>  
 <span data-ttu-id="e2ba3-106">L'exemple suivant ouvre un document WordprocessingML Office Open XML, recherche les parties document et style du package, puis exécute une requête qui recherche le nom du style par défaut.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="e2ba3-107">Pour plus d’informations sur les packages de documents Office Open XML et leurs parties, consultez [Détails des documents WordprocessingML Office Open XML (Visual Basic)](details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="e2ba3-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="e2ba3-108">La requête recherche un nœud nommé `w:style` qui possède un attribut nommé `w:type` avec la valeur « paragraph » et un attribut nommé `w:default` avec la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="e2ba3-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="e2ba3-109">Étant donné qu'il n'y aura qu'un seul nœud XML avec ces attributs, la requête utilise l'opérateur <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> pour convertir une collection en singleton.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="e2ba3-110">Elle obtient ensuite la valeur de l'attribut avec le nom `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="e2ba3-111">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="e2ba3-112">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2ba3-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e2ba3-113">Code</span><span class="sxs-lookup"><span data-stu-id="e2ba3-113">Code</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="e2ba3-114">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e2ba3-114">Comments</span></span>  
 <span data-ttu-id="e2ba3-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e2ba3-115">This example produces the following output:</span></span>  
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="e2ba3-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e2ba3-116">Next Steps</span></span>  
 <span data-ttu-id="e2ba3-117">Dans l'exemple suivant, nous allons créer une requête similaire qui recherche tous les paragraphes d'un document et leurs styles :</span><span class="sxs-lookup"><span data-stu-id="e2ba3-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="e2ba3-118">Récupération des paragraphes et de leurs styles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ba3-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2ba3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2ba3-119">See also</span></span>

- [<span data-ttu-id="e2ba3-120">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ba3-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
