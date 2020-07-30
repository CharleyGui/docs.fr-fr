---
title: Comment récupérer la valeur d’un élément (LINQ to XML) (C#)
description: Découvrez comment obtenir la valeur des éléments. Consultez les exemples utilisant la conversion de chaînes, la conversion d’entiers et la propriété Value.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301539"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Comment récupérer la valeur d’un élément (LINQ to XML) (C#)

Cet article montre comment récupérer la valeur des éléments. Il existe deux façons principales d’acquérir la valeur :

- Effectuez un cast d’un <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> d’un vers le type souhaité. L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.

- Utilisez les <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Propriétés ou. Vous pouvez également définir la valeur à l’aide de ces propriétés.

Avec C#, la conversion est généralement la meilleure approche. Si vous effectuez un cast de l’élément ou de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un élément (ou attribut) qui peut ou non exister. Le [dernier exemple](#element-might-not-exist-example) de cet article montre que la conversion est plus simple dans le cas où l’élément n’existe peut-être pas. Toutefois, vous ne pouvez pas définir le contenu d'un élément par le biais de la conversion, comme vous le pouvez par le biais de la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.  
  
## <a name="string-cast-example"></a>Exemple de conversion de chaîne  
 Pour récupérer la valeur d’un élément, effectuez un cast de l' <xref:System.Xml.Linq.XElement> objet vers le type souhaité. Vous pouvez convertir un élément en chaîne, comme suit :  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>Exemple de cast d’entier  
 Vous pouvez également convertir des éléments vers des types autres que des chaînes. Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.  
  
## <a name="value-property-example"></a>Exemple de propriété Value  
 Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>L’élément n’existe peut-être pas
 Parfois, vous tentez de récupérer la valeur d’un élément même si vous n’êtes pas certain qu’il existe. Dans ce cas, lorsque vous assignez l’élément casté à un type de référence Nullable ou à un type de valeur Nullable, si l’élément n’existe pas, la variable assignée a la valeur `null` . Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
