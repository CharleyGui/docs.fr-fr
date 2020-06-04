---
title: Événements LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368814"
---
# <a name="linq-to-xml-events-visual-basic"></a>Événements de LINQ to XML (Visual Basic)
Les événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’être averti quand une arborescence XML est modifiée.  
  
 Vous pouvez ajouter des événements à une instance de n'importe quel objet <xref:System.Xml.Linq.XObject>. Le gestionnaire d'événements recevra alors des événements en cas de modification apportée à cet objet <xref:System.Xml.Linq.XObject> et à l'un de ses descendants. Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.  
  
 Pour obtenir des exemples d’événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consultez <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Types et événements  
 Vous utilisez les types suivants lorsque vous travaillez avec des événements :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Spécifie le type d'événement lorsqu'un événement est déclenché pour un objet <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Fournit des données pour les événements <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.|  
  
 Les événements suivants sont déclenchés lorsque vous modifiez une arborescence XML :  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Se produit juste avant que cet objet <xref:System.Xml.Linq.XObject> ou l'un de ses descendants ne change.|  
|<xref:System.Xml.Linq.XObject.Changed>|Se produit lorsqu'un objet <xref:System.Xml.Linq.XObject> ou l'un des ses descendants a changé.|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML. Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture. Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.  
  
### <a name="code"></a>Code  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Commentaires  
 Ce code génère la sortie suivante :  
  
```console  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](advanced-linq-to-xml-programming.md)
