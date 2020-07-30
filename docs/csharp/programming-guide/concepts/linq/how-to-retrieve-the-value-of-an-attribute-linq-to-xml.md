---
title: Comment récupérer la valeur d’un attribut (LINQ to XML) (C#)
description: Découvrez comment obtenir la valeur d’un attribut. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301552"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Comment récupérer la valeur d’un attribut (LINQ to XML) (C#)
Cette rubrique montre comment obtenir la valeur d'attributs. Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié. En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>. Toutefois, la conversion est généralement la meilleure approche. Si vous effectuez un cast de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un attribut qui peut ou non exister. Pour obtenir des exemples de cette technique, consultez [Comment récupérer la valeur d’un élément (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms. Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
