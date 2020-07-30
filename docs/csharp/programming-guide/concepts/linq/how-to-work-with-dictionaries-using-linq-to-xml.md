---
title: Comment utiliser des dictionnaires à l’aide d’LINQ to XML (C#)
description: Découvrez comment utiliser les dictionnaires à l’aide de LINQ to XML. Consultez les exemples de conversion de dictionnaires au format XML et XML en d’autres structures de données.
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: bdba7a2b3dfc16fab1e239ac804c317dfefb7d9e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302618"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Comment utiliser des dictionnaires à l’aide d’LINQ to XML (C#)
Il est souvent plus pratique de convertir différentes structures de données au format XML et du format XML en d’autres structures de données. Cette rubrique présente une implémentation spécifique de cette approche générale en convertissant un objet <xref:System.Collections.Generic.Dictionary%602> au format XML et inversement.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une forme de construction fonctionnelle dans laquelle une requête projette de nouveaux objets <xref:System.Xml.Linq.XElement> et la collection obtenue est passée comme argument au constructeur de l’objet <xref:System.Xml.Linq.XElement> Root.  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant crée un dictionnaire à partir de données XML.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
