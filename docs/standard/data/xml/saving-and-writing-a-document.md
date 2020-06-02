---
title: Enregistrement et écriture d'un document
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289042"
---
# <a name="saving-and-writing-a-document"></a>Enregistrement et écriture d'un document
Lorsque vous chargez et enregistrez un objet <xref:System.Xml.XmlDocument>, le document sauvegardé peut varier de l'original dans les points suivants :  
  
- Si la propriété <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> est définie sur `true` avant l'appel à la méthode <xref:System.Xml.XmlDocument.Save%2A>, l'espace blanc du document est conservé à la sortie. Si cette propriété est définie sur `false`, l'objet <xref:System.Xml.XmlDocument> met automatiquement la sortie en retrait.  
  
- Tous les espaces blancs entre les attributs sont réduits à un espace simple.  
  
- L'espace blanc entre les éléments est modifié. Seuls les espaces blancs significatifs sont conservés. Mais lors de l'enregistrement du document, celui-ci utilise le mode  <xref:System.Xml.XmlTextWriter> **Indenting** par défaut pour imprimer clairement la sortie et la rendre plus lisible.  
  
- Le caractère guillemet qui entoure les valeurs d'attribut est remplacé par défaut par le guillemet double. Vous pouvez utiliser la propriété <xref:System.Xml.XmlTextReader.QuoteChar%2A> sur <xref:System.Xml.XmlTextWriter> pour définir le caractère guillemet sur un guillemet double ou un guillemet simple.  
  
- Par défaut, des entités de caractère numérique telles que `{` sont développées.  
  
- La marque d'ordre d'octet se trouvant dans le document d'entrée n'est pas conservée. L'encodage UCS-2 est enregistré comme de l'encodage UTF-8 à moins que vous ne créiez explicitement une déclaration XML qui spécifie un autre encodage.  
  
- Si vous souhaitez écrire l'objet <xref:System.Xml.XmlDocument> dans un fichier ou un flux, la sortie écrite est identique au contenu du document. Ainsi, l'objet <xref:System.Xml.XmlDeclaration> n'est écrit que s'il en existe un dans le document et l'encodage employé pour l'écriture du document est le même que celui du nœud de déclaration.  
  
## <a name="writing-an-xmldeclaration"></a>Écriture d'une XmlDeclaration  
 Les membres <xref:System.Xml.XmlDocument> et <xref:System.Xml.XmlDeclaration> de la propriété <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlNode.WriteTo%2A> et les méthodes <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlDocument.Save%2A> et <xref:System.Xml.XmlDocument.WriteContentTo%2A> créent une déclaration XML.  
  
 Pour les propriétés <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A> et les méthodes <xref:System.Xml.XmlDocument.WriteContentTo%2A>, l'encodage écrit dans la déclaration XML est prélevé du nœud <xref:System.Xml.XmlDeclaration>. S’il n’y a aucun <xref:System.Xml.XmlDeclaration> nœud, <xref:System.Xml.XmlDeclaration> n’est pas écrit. S’il n’y a pas d’encodage dans le <xref:System.Xml.XmlDeclaration> nœud, l’encodage n’est pas écrit dans la déclaration XML.  
  
 Les méthodes <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> et <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> écrivent toujours un objet <xref:System.Xml.XmlDeclaration>. Ces méthodes prennent l'encodage du writer dans lequel elles écrivent. Ainsi, la valeur d'encodage du writer remplace l'encodage du document et de l'objet <xref:System.Xml.XmlDeclaration>. Par exemple, le code suivant n'écrit pas un encodage dans la déclaration XML trouvée dans le fichier de sortie `out.xml`.  
  
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
  
 Dans le cas de la méthode <xref:System.Xml.XmlDocument.Save%2A>, la déclaration XML est écrite à l'aide de la méthode <xref:System.Xml.XmlWriter.WriteStartDocument%2A> de la classe <xref:System.Xml.XmlWriter>. Par conséquent, le remplacement de la méthode <xref:System.Xml.XmlWriter.WriteStartDocument%2A> modifie la manière dont le début du document est écrit.  
  
 Pour les <xref:System.Xml.XmlDeclaration> membres de <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> et <xref:System.Xml.XmlNode.InnerXml%2A> , si la <xref:System.Xml.XmlDeclaration.Encoding%2A> propriété n’est pas définie, aucun encodage n’est écrit. Dans le cas contraire, l’encodage écrit dans la déclaration XML est le même que celui trouvé dans la <xref:System.Xml.XmlDeclaration.Encoding%2A> propriété.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Écriture de contenu de document à l'aide de la propriété OuterXml  
 La propriété <xref:System.Xml.XmlNode.OuterXml%2A> est une extension Microsoft des normes DOM (Document Object Model) XML du W3C (World Wide Web Consortium). La propriété <xref:System.Xml.XmlNode.OuterXml%2A> permet d'obtenir le balisage de l'ensemble du document XML ou d'un seul nœud et de ses nœuds enfants. La propriété <xref:System.Xml.XmlNode.OuterXml%2A> retourne le balisage représentant le nœud donné et tous ses nœuds enfants.  
  
 L'exemple de code suivant montre comment enregistrer l'intégralité d'un document sous la forme d'une chaîne.  
  
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
  
 L'exemple de code suivant montre comment n'enregistrer que l'élément de document.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 En revanche, vous pouvez utiliser la propriété <xref:System.Xml.XmlNode.InnerText%2A> pour obtenir le contenu des nœuds enfants.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
