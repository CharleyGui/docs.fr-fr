---
title: Comment récupérer la valeur d’un élément (LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805836"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Comment récupérer la valeur d’un élément (LINQ à XML) (C)

Cet article montre comment obtenir la valeur des éléments. Il y a deux façons principales d’obtenir la valeur :

- Lancer <xref:System.Xml.Linq.XElement> un <xref:System.Xml.Linq.XAttribute> ou un au type désiré. L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.

- Utilisez <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> les <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> propriétés ou les propriétés. Vous pouvez également définir la valeur en utilisant ces propriétés.

Avec C, le casting est généralement la meilleure approche. Si vous lancez l’élément ou l’attribut à un type de valeur nul, le code est plus simple à écrire lors de la récupération de la valeur d’un élément (ou attribut) qui pourrait ou ne pourrait pas exister. Le [dernier exemple](#element-might-not-exist-example) de cet article démontre que le casting est plus simple dans le cas où l’élément pourrait ne pas exister. Toutefois, vous ne pouvez pas définir le contenu d'un élément par le biais de la conversion, comme vous le pouvez par le biais de la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.  
  
## <a name="string-cast-example"></a>Exemple de lance-cordes  
 Pour récupérer la valeur d’un élément, jetez l’objet <xref:System.Xml.Linq.XElement> sur le type désiré. Vous pouvez jeter un élément à une chaîne, comme suit:  
  
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
  
## <a name="integer-cast-example"></a>Integer fait l’exemple  
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
  
## <a name="value-property-example"></a>Exemple de propriété de valeur  
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
  
## <a name="element-might-not-exist-example"></a>L’élément n’existe peut-être pas d’exemple
 Parfois, vous essayez de récupérer la valeur d’un élément, même si vous n’êtes pas sûr si elle existe. Dans ce cas, lorsque vous attribuez l’élément castré à un type de référence nul ou à `null`un type de valeur nul, si l’élément n’existe pas, la variable assignée est définie à . Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.  
  
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
