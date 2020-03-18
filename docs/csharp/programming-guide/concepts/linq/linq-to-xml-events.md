---
title: Événements LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253172"
---
# <a name="linq-to-xml-events-c"></a>Événements LINQ to XML (C#)
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
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  
 Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML. Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture. Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Commentaires  
 Ce code génère la sortie suivante :  
  
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
  