---
title: Sérialisation avec une déclaration XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350632"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serializing with an XML Declaration (Visual Basic)
Cette rubrique décrit comment contrôler si la sérialisation génère une déclaration XML.  
  
## <a name="xml-declaration-generation"></a>Génération de déclaration XML  
 La sérialisation vers un objet <xref:System.IO.File> ou <xref:System.IO.TextWriter> à l'aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>génère une déclaration XML. Lorsque vous sérialisez vers un objet <xref:System.Xml.XmlWriter>, les paramètres de writer (spécifiés dans un objet <xref:System.Xml.XmlWriterSettings>) déterminent si une déclaration XML est générée ou non.  
  
 Si vous sérialisez vers une chaîne à l'aide de la méthode `ToString`, le code XML résultant n'inclura pas de déclaration XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Sérialisation avec une déclaration XML  
 L'exemple suivant crée un objet <xref:System.Xml.Linq.XElement>, enregistre le document dans un fichier, puis imprime le fichier sur la console :  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Sérialisation sans déclaration XML  
 L'exemple suivant montre comment enregistrer un objet <xref:System.Xml.Linq.XElement> dans un objet <xref:System.Xml.XmlWriter>.  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
