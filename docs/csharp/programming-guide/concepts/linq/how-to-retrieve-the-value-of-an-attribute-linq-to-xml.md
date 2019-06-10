---
title: 'Procédure : Récupérer la valeur d’un attribut (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 94cab43571f7ade55155e7925975f253e452ceb7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484997"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Procédure : Récupérer la valeur d’un attribut (LINQ to XML) (C#)
Cette rubrique montre comment obtenir la valeur d'attributs. Il existe pour cela deux méthodes : vous pouvez caster un <xref:System.Xml.Linq.XAttribute> en un type souhaité. L’opérateur de conversion explicite convertit alors le contenu de l’élément ou de l’attribut vers le type spécifié. En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>. Toutefois, la conversion est généralement la meilleure approche. Si vous convertissez l'attribut vers un type Nullable, le code est plus simple à écrire lors de la récupération de la valeur d'un attribut qui peut exister ou ne pas exister. Pour obtenir des exemples de cette technique, consultez [Guide pratique pour récupérer la valeur d’un élément (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Exemple  
 Pour récupérer la valeur d'un attribut, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms. Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
