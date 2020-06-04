---
title: 'Procédure : rechercher un élément enfant (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 1b0a3af5a1679643d73649f9de6b1dc3c44cbb0d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357165"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a>Comment : Rechercher un élément enfant (XPath-LINQ to XML) (Visual Basic)
Cette rubrique compare l’axe des éléments enfants XPath à la [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> méthode.  
  
 L'expression XPath est `DeliveryNotes`.  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche l'élément enfant `DeliveryNotes`.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```console
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
