---
title: 'Procédure : Rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 1adbbb6dd074ffcb39269a800024e444cf8791d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253759"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Procédure : Rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (C#)
Parfois, vous souhaitez rechercher des éléments en fonction de leur position. Vous pourriez souhaiter rechercher le deuxième élément, ou les troisième, quatrième et cinquième éléments.  
  
 L’expression XPath est la suivante :  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Il existe deux approches pour l'écriture de cette requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] d'une manière différée. Vous pouvez utiliser les opérateurs <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A>, ou vous pouvez utiliser la surcharge <xref:System.Linq.Enumerable.Where%2A> qui prend un index. Lorsque vous utilisez la surcharge <xref:System.Linq.Enumerable.Where%2A>, vous utilisez une expression lambda qui prend deux arguments. L'exemple suivant illustre les deux méthodes de sélection basée sur la position.  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche les deuxième, troisième et quatrième éléments `Test`. Le résultat est une collection d’éléments.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration de test (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```output  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
