---
title: Comment récupérer la valeur superficielle d’un élément (C#)
description: Découvrez comment obtenir la valeur superficielle d’un élément. La valeur superficielle est uniquement pour l’élément spécifique.
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301578"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Comment récupérer la valeur superficielle d’un élément (C#)
Cette rubrique montre comment obtenir la valeur superficielle d'un élément. La valeur superficielle est la valeur de l’élément spécifique uniquement, par opposition à la valeur profonde, qui inclut les valeurs de tous les éléments descendants concaténés dans une chaîne unique.  
  
 Lorsque vous extrayez la valeur d'un élément par le biais d'une conversion ou en utilisant la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>, vous extrayez une valeur profonde. Pour extraire la valeur superficielle, vous pouvez utiliser la méthode d'extension `ShallowValue`, comme dans l'exemple suivant. L'extraction de la valeur superficielle est utile lorsque vous voulez sélectionner des éléments en fonction de leur contenu.  
  
 L'exemple suivant déclare une méthode d'extension qui extrait la valeur superficielle d'un élément. Il utilise ensuite la méthode d’extension dans une requête pour répertorier tous les éléments qui contiennent une valeur calculée.  
  
## <a name="example"></a>Exemple  
 Le fichier texte suivant, Report.xml, est la source pour cet exemple.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
