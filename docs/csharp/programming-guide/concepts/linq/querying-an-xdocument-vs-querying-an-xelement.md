---
title: Interrogation d’un XDocument et interrogation d’un XElement (C#)
description: En savoir plus sur les différences entre l’interrogation d’un XDocument et l’interrogation d’un XElement. Passez en revue les exemples de code qui illustrent ces différences.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300317"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Interrogation d’un XDocument et interrogation d’un XElement (C#)
Lorsque vous chargez un document par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, vous remarquerez que vous devez écrire des requêtes de manière légèrement différente comparé au chargement par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Comparaison de XDocument.Load et XElement.Load  
 Lorsque vous chargez un document XML dans <xref:System.Xml.Linq.XElement> par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, l'objet <xref:System.Xml.Linq.XElement> à la racine de l'arborescence XML contient l'élément racine du document chargé. Toutefois, lorsque vous chargez le même document XML dans un objet <xref:System.Xml.Linq.XDocument> par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, la racine de l'arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l'élément racine du document chargé est le nœud <xref:System.Xml.Linq.XElement> enfant autorisé de l'objet <xref:System.Xml.Linq.XDocument>. Les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] opèrent relativement au nœud racine.  
  
 Ce premier exemple charge une arborescence XML à l'aide de <xref:System.Xml.Linq.XElement.Load%2A>. Il interroge ensuite les éléments enfants de la racine de l'arborescence.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Comme prévu, cet exemple produit la sortie suivante :  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 L'exemple suivant est identique au précédent, hormis le fait que l'arborescence XML est chargée dans un objet <xref:System.Xml.Linq.XDocument> au lieu d'un objet <xref:System.Xml.Linq.XElement>.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.  
  
 L'une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d'accéder aux méthodes d'axe, comme suit :  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Cette requête s'exécute maintenant de la même manière que la requête sur l'arborescence enracinée dans <xref:System.Xml.Linq.XElement>. L'exemple produit la sortie suivante :  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  