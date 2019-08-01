---
title: 'Procédure : Récupérer un seul attribut (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 635644783153765d61aff3c00fe16860642c29f1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710526"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Procédure : Récupérer un seul attribut (LINQ to XML) (Visual Basic)
Cette rubrique explique comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut. Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.  
  
 La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.  
  
## <a name="example"></a>Exemples  
 L'exemple suivant utilise la méthode <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 Cet exemple recherche tous les descendants dans l'arborescence nommés `Phone`, puis recherche l'attribut nommé `type`.  
  
 Ce code génère la sortie suivante :  
  
```  
home  
work  
```  
  
## <a name="example"></a>Exemple  
 Si vous souhaitez récupérer la valeur de l'attribut vous pouvez le convertir, comme vous le feriez avec des objets <xref:System.Xml.Linq.XElement>. Cela est illustré par l'exemple suivant.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit des opérateurs de conversion explicites pour la classe <xref:System.Xml.Linq.XAttribute> vers `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.  
  
## <a name="example"></a>Exemples  
 L'exemple suivant illustre le même code pour un attribut qui est dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
