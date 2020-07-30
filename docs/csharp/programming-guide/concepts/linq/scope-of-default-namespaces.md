---
title: Portée des espaces de noms par défaut en C#
description: Découvrez comment interroger les espaces de noms XML par défaut en LINQ to XML en C#. Utilisez une variable XNamespace et le nom local pour donner un nom qualifié à la requête.
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 912e47099f89daa9b80ac58b422d39d598509ac9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302397"
---
# <a name="scope-of-default-namespaces-in-c"></a>Portée des espaces de noms par défaut en C\#
Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes. Si vous avez du code XML qui est dans un espace de noms par défaut, vous devez déclarer une variable <xref:System.Xml.Linq.XNamespace> et la combiner avec le nom local afin de créer un nom complet utilisable dans la requête.  
  
 L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.  
  
 Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.  
  
 Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.  
  
### <a name="code"></a>Code  
  
```csharp  
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
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère le résultat suivant :  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.  
  
 Par rapport à l'exemple de code incorrect illustré ci-dessus, l'approche appropriée, lors de l'utilisation du langage C#, consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace> et à l'utiliser lors de la spécification d'objets <xref:System.Xml.Linq.XName>. Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.  
  
### <a name="code"></a>Code  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère le résultat suivant :  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
