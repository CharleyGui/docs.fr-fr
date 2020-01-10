---
title: Extraction de nœuds triés par l'index
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 72e866e43b556d8534024a219d924b1f372ed073
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710516"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="78de7-102">Extraction de nœuds triés par l'index</span><span class="sxs-lookup"><span data-stu-id="78de7-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="78de7-103">Le DOM (Document Object Model) XML du World Wide Web Consortium (W3C) décrit également un NodeList, qui permet de gérer une liste triée de nœuds, par opposition à l’ensemble non trié que gère **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="78de7-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="78de7-104">Dans le Microsoft .NET Framework, ce NodeList est appelé **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="78de7-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="78de7-105">Les méthodes et propriétés qui retournent **XmlNodeList** sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="78de7-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="78de7-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="78de7-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="78de7-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="78de7-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="78de7-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="78de7-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="78de7-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="78de7-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="78de7-110">**XmlNodeList** possède une propriété **Count** qui peut être utilisée pour tracer des boucles pour itérer au sein des nœuds de **XmlNodeList**, comme le montre l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="78de7-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
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
  
 <span data-ttu-id="78de7-111">En plus de la propriété **Count**, il existe une méthode **GetEnumerator** qui exécute une itération du type `foreach` sur la collection de nœuds de **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="78de7-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="78de7-112">L'exemple de code suivant illustre l'utilisation de l'instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="78de7-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="78de7-113">Pour plus d'informations sur les propriétés et méthodes disponibles dans **XmlNodeList**, consultez <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="78de7-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78de7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78de7-114">See also</span></span>

- [<span data-ttu-id="78de7-115">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="78de7-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
