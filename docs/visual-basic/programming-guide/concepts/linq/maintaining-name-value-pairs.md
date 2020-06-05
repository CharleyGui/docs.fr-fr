---
title: Maintenance de paires nom-valeur
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 1e30f010311dda393f65b1424e56f5b5ad014963
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389215"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Gestion des paires nom/valeur (Visual Basic)
De nombreuses applications doivent maintenir des informations qu'il est préférable de conserver sous forme de paires nom/valeur. Il peut s'agir d'informations de configuration ou de paramètres globaux. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] contient des méthodes qui facilitent la maintenance d'un ensemble de paires nom/valeur. Vous pouvez conserver les informations en tant qu'attributs ou en tant qu'ensemble d'éléments enfants.  
  
 L'une des différences est qu'il ne peut y avoir qu'un seul attribut avec un nom donné pour un élément. Cette limitation ne s'applique pas aux éléments enfants.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue et SetElementValue  
 Les deux méthodes qui facilitent la conservation de paires nom/valeur sont <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> et <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Ces deux méthodes ont une sémantique similaire.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> peut ajouter, modifier ou supprimer des attributs d'un élément.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut qui n'existe pas, la méthode crée un nouvel attribut et l'ajoute à l'élément spécifié.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut existant et avec du contenu spécifié, le contenu de l'attribut est remplacé par le contenu spécifié.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut existant et que vous spécifiez une valeur Null pour le contenu, l'attribut est supprimé de son parent.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> peut ajouter, modifier ou supprimer des éléments enfants d'un élément.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément enfant qui n'existe pas, la méthode crée un nouvel élément et l'ajoute à l'élément spécifié.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément existant et avec du contenu spécifié, le contenu de l'élément est remplacé par le contenu spécifié.  
  
- Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément existant et que vous spécifiez une valeur Null pour le contenu, l'élément est supprimé de son parent.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un élément sans attribut. Il utilise ensuite la méthode <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> pour créer et maintenir une liste de paires nom/valeur.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un élément sans élément enfant. Il utilise ensuite la méthode <xref:System.Xml.Linq.XElement.SetElementValue%2A> pour créer et maintenir une liste de paires nom/valeur.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Modification d’arborescences XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
