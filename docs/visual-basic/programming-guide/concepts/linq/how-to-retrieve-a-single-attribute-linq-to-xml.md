---
title: 'Procédure : récupérer un seul attribut (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397854"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Comment : récupérer un seul attribut (LINQ to XML) (Visual Basic)
Cette rubrique explique comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut. Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.  
  
 La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.  
  
## <a name="example"></a>Exemple  
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
  
```console  
home  
work  
```  
  
## <a name="example"></a>Exemple  
 Si vous souhaitez récupérer la valeur de l'attribut vous pouvez le convertir, comme vous le feriez avec des objets <xref:System.Xml.Linq.XElement>. l’exemple ci-dessous illustre ce cas de figure.  
  
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
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit des opérateurs de conversion explicites pour la classe <xref:System.Xml.Linq.XAttribute> vers `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.  
  
## <a name="example"></a>Exemple  
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
  
```console  
home  
work  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (Visual Basic)](linq-to-xml-axes.md)
