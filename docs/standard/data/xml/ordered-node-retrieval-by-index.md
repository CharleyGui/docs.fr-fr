---
title: Extraction de nœuds triés par l'index
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e4847dd6bc05127799cb6d8424a8fdb63fbc0f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590060"
---
# <a name="ordered-node-retrieval-by-index"></a>Extraction de nœuds triés par l'index
Le DOM (Document Object Model) XML du World Wide Web Consortium (W3C) décrit également un NodeList, qui permet de gérer une liste triée de nœuds, par opposition à l’ensemble non trié que gère **XmlNamedNodeMap**. Dans le Microsoft .NET Framework, ce NodeList est appelé **XmlNodeList**. Les méthodes et propriétés qui retournent **XmlNodeList** sont les suivantes :  
  
- XmlNode.ChildNodes  
  
- XmlDocument.GetElementsByTagName  
  
- XmlElement.GetElementsByTagName  
  
- XmlNode.SelectNodes  
  
 **XmlNodeList** possède une propriété **Count** qui peut être utilisée pour tracer des boucles pour itérer au sein des nœuds de **XmlNodeList**, comme le montre l'exemple de code suivant :  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 En plus de la propriété **Count**, il existe une méthode **GetEnumerator** qui exécute une itération du type `foreach` sur la collection de nœuds de **XmlNodeList**. L'exemple de code suivant illustre l'utilisation de l'instruction `foreach`.  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 Pour plus d'informations sur les propriétés et méthodes disponibles dans **XmlNodeList**, consultez <xref:System.Xml.XmlNodeList>.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
