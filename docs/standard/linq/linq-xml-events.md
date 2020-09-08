---
title: Événements de LINQ to XML-LINQ to XML
description: Découvrez comment utiliser des événements XML pour surveiller les modifications apportées à une arborescence XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 755aa1a449e873a2c4f5b17d4df3eee7ecfa9969
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553340"
---
# <a name="linq-to-xml-events-linq-to-xml"></a>Événements de LINQ to XML (LINQ to XML)

LINQ to XML événements vous permettent d’être averti lorsqu’une arborescence XML est modifiée.

Vous pouvez ajouter des événements à n’importe quelle instance de n’importe laquelle <xref:System.Xml.Linq.XObject> . Le gestionnaire d'événements recevra alors des événements en cas de modification apportée à cet objet <xref:System.Xml.Linq.XObject> et à l'un de ses descendants. Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.

Pour obtenir des exemples d’événements de LINQ to XML, consultez <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed> .

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

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a>Exemple : utiliser des événements pour conserver un total approprié lorsque des éléments sont modifiés

Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML. Par exemple, vous souhaiterez peut-être conserver un total de facture qui est la somme des éléments de ligne de la facture. Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.

```csharp
XElement root = new XElement("Root",
    new XElement("Total", "0"),
    new XElement("Items")
);
XElement total = root.Element("Total");
XElement items = root.Element("Items");
items.Changed += (object sender, XObjectChangeEventArgs cea) =>
{
    switch (cea.ObjectChange)
    {
        case XObjectChange.Add:
            if (sender is XElement)
                total.Value = ((int)total + (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();
            break;
        case XObjectChange.Remove:
            if (sender is XElement)
                total.Value = ((int)total - (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();
            break;
    }
    Console.WriteLine("Changed {0} {1}",
      sender.GetType().ToString(), cea.ObjectChange.ToString());
};
items.SetElementValue("Item1", 25);
items.SetElementValue("Item2", 50);
items.SetElementValue("Item2", 75);
items.SetElementValue("Item3", 133);
items.SetElementValue("Item1", null);
items.SetElementValue("Item4", 100);
Console.WriteLine("Total:{0}", (int)total);
Console.WriteLine(root);
```

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

Cet exemple produit la sortie suivante :

```output
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
