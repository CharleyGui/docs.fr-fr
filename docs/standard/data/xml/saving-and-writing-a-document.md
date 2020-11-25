---
title: Enregistrement et écriture d'un document
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 14497bb5b027209c4707eab9bcf1b60f85740dfd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697556"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="8d101-102">Enregistrement et écriture d'un document</span><span class="sxs-lookup"><span data-stu-id="8d101-102">Saving and Writing a Document</span></span>

<span data-ttu-id="8d101-103">Lorsque vous chargez et enregistrez un objet <xref:System.Xml.XmlDocument>, le document sauvegardé peut varier de l'original dans les points suivants :</span><span class="sxs-lookup"><span data-stu-id="8d101-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="8d101-104">Si la propriété <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> est définie sur `true` avant l'appel à la méthode <xref:System.Xml.XmlDocument.Save%2A>, l'espace blanc du document est conservé à la sortie. Si cette propriété est définie sur `false`, l'objet <xref:System.Xml.XmlDocument> met automatiquement la sortie en retrait.</span><span class="sxs-lookup"><span data-stu-id="8d101-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="8d101-105">Tous les espaces blancs entre les attributs sont réduits à un espace simple.</span><span class="sxs-lookup"><span data-stu-id="8d101-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="8d101-106">L'espace blanc entre les éléments est modifié.</span><span class="sxs-lookup"><span data-stu-id="8d101-106">The white space between elements is changed.</span></span> <span data-ttu-id="8d101-107">Seuls les espaces blancs significatifs sont conservés.</span><span class="sxs-lookup"><span data-stu-id="8d101-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="8d101-108">Mais lors de l'enregistrement du document, celui-ci utilise le mode  <xref:System.Xml.XmlTextWriter> **Indenting** par défaut pour imprimer clairement la sortie et la rendre plus lisible.</span><span class="sxs-lookup"><span data-stu-id="8d101-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="8d101-109">Le caractère guillemet qui entoure les valeurs d'attribut est remplacé par défaut par le guillemet double.</span><span class="sxs-lookup"><span data-stu-id="8d101-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="8d101-110">Vous pouvez utiliser la propriété <xref:System.Xml.XmlTextReader.QuoteChar%2A> sur <xref:System.Xml.XmlTextWriter> pour définir le caractère guillemet sur un guillemet double ou un guillemet simple.</span><span class="sxs-lookup"><span data-stu-id="8d101-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="8d101-111">Par défaut, des entités de caractère numérique telles que `{` sont développées.</span><span class="sxs-lookup"><span data-stu-id="8d101-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="8d101-112">La marque d'ordre d'octet se trouvant dans le document d'entrée n'est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="8d101-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="8d101-113">L'encodage UCS-2 est enregistré comme de l'encodage UTF-8 à moins que vous ne créiez explicitement une déclaration XML qui spécifie un autre encodage.</span><span class="sxs-lookup"><span data-stu-id="8d101-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="8d101-114">Si vous souhaitez écrire l'objet <xref:System.Xml.XmlDocument> dans un fichier ou un flux, la sortie écrite est identique au contenu du document.</span><span class="sxs-lookup"><span data-stu-id="8d101-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="8d101-115">Ainsi, l'objet <xref:System.Xml.XmlDeclaration> n'est écrit que s'il en existe un dans le document et l'encodage employé pour l'écriture du document est le même que celui du nœud de déclaration.</span><span class="sxs-lookup"><span data-stu-id="8d101-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="8d101-116">Écriture d'une XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="8d101-116">Writing an XmlDeclaration</span></span>  

 <span data-ttu-id="8d101-117">Les membres <xref:System.Xml.XmlDocument> et <xref:System.Xml.XmlDeclaration> de la propriété <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlNode.WriteTo%2A> et les méthodes <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlDocument.Save%2A> et <xref:System.Xml.XmlDocument.WriteContentTo%2A> créent une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="8d101-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="8d101-118">Pour les propriétés <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A> et les méthodes <xref:System.Xml.XmlDocument.WriteContentTo%2A>, l'encodage écrit dans la déclaration XML est prélevé du nœud <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="8d101-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="8d101-119">S’il n’y a aucun <xref:System.Xml.XmlDeclaration> nœud, <xref:System.Xml.XmlDeclaration> n’est pas écrit. S’il n’y a pas d’encodage dans le <xref:System.Xml.XmlDeclaration> nœud, l’encodage n’est pas écrit dans la déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="8d101-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="8d101-120">Les méthodes <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> et <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> écrivent toujours un objet <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="8d101-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="8d101-121">Ces méthodes prennent l'encodage du writer dans lequel elles écrivent.</span><span class="sxs-lookup"><span data-stu-id="8d101-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="8d101-122">Ainsi, la valeur d'encodage du writer remplace l'encodage du document et de l'objet <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="8d101-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="8d101-123">Par exemple, le code suivant n'écrit pas un encodage dans la déclaration XML trouvée dans le fichier de sortie `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="8d101-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="8d101-124">Dans le cas de la méthode <xref:System.Xml.XmlDocument.Save%2A>, la déclaration XML est écrite à l'aide de la méthode <xref:System.Xml.XmlWriter.WriteStartDocument%2A> de la classe <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="8d101-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="8d101-125">Par conséquent, le remplacement de la méthode <xref:System.Xml.XmlWriter.WriteStartDocument%2A> modifie la manière dont le début du document est écrit.</span><span class="sxs-lookup"><span data-stu-id="8d101-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="8d101-126">Pour les <xref:System.Xml.XmlDeclaration> membres de <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> et <xref:System.Xml.XmlNode.InnerXml%2A> , si la <xref:System.Xml.XmlDeclaration.Encoding%2A> propriété n’est pas définie, aucun encodage n’est écrit. Dans le cas contraire, l’encodage écrit dans la déclaration XML est le même que celui trouvé dans la <xref:System.Xml.XmlDeclaration.Encoding%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="8d101-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="8d101-127">Écriture de contenu de document à l'aide de la propriété OuterXml</span><span class="sxs-lookup"><span data-stu-id="8d101-127">Writing Document Content Using the OuterXml Property</span></span>  

 <span data-ttu-id="8d101-128">La propriété <xref:System.Xml.XmlNode.OuterXml%2A> est une extension Microsoft des normes DOM (Document Object Model) XML du W3C (World Wide Web Consortium).</span><span class="sxs-lookup"><span data-stu-id="8d101-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="8d101-129">La propriété <xref:System.Xml.XmlNode.OuterXml%2A> permet d'obtenir le balisage de l'ensemble du document XML ou d'un seul nœud et de ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="8d101-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="8d101-130">La propriété <xref:System.Xml.XmlNode.OuterXml%2A> retourne le balisage représentant le nœud donné et tous ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="8d101-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="8d101-131">L'exemple de code suivant montre comment enregistrer l'intégralité d'un document sous la forme d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8d101-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="8d101-132">L'exemple de code suivant montre comment n'enregistrer que l'élément de document.</span><span class="sxs-lookup"><span data-stu-id="8d101-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="8d101-133">En revanche, vous pouvez utiliser la propriété <xref:System.Xml.XmlNode.InnerText%2A> pour obtenir le contenu des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="8d101-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d101-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d101-134">See also</span></span>

- [<span data-ttu-id="8d101-135">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="8d101-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
