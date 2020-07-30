---
title: Comment écrire des requêtes sur du code XML dans des espaces de noms (C#)
description: Découvrez comment écrire des requêtes sur du code XML dans des espaces de noms. Pour ces requêtes, vous devez utiliser les objets XName qui possèdent l’espace de noms correct.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303177"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Comment écrire des requêtes sur du code XML dans des espaces de noms (C#)
Pour écrire des requêtes sur du code XML qui est dans un espace de noms, vous devez utiliser des objets <xref:System.Xml.Linq.XName> qui ont l'espace de noms correct.  
  
 Pour C#, l'approche la plus courante consiste à initialiser un objet <xref:System.Xml.Linq.XNamespace> à l'aide d'une chaîne contenant l'URI, puis à utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local.  
  
 Le premier ensemble d’exemples de cette rubrique montre comment créer une arborescence XML dans un espace de noms par défaut. Le second ensemble illustre la création d’une arborescence XML dans un espace de noms avec un préfixe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une arborescence XML qui est dans un espace de noms par défaut. Il récupère ensuite une collection d'éléments.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Exemple  
 En C#, vous écrivez des requêtes de la même manière, que ce soit sur une arborescence XML qui utilise un espace de noms avec un préfixe ou sur une arborescence XML avec un espace de noms par défaut.  
  
 L’exemple suivant crée une arborescence XML qui est dans un espace de noms avec un préfixe. Il récupère ensuite une collection d'éléments.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
