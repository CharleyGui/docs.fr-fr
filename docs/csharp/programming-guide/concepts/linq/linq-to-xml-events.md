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
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="095fa-102">Événements LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="095fa-102">LINQ to XML Events (C#)</span></span>
<span data-ttu-id="095fa-103">Les événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’être averti quand une arborescence XML est modifiée.</span><span class="sxs-lookup"><span data-stu-id="095fa-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="095fa-104">Vous pouvez ajouter des événements à une instance de n'importe quel objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="095fa-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="095fa-105">Le gestionnaire d'événements recevra alors des événements en cas de modification apportée à cet objet <xref:System.Xml.Linq.XObject> et à l'un de ses descendants.</span><span class="sxs-lookup"><span data-stu-id="095fa-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="095fa-106">Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="095fa-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="095fa-107">Pour obtenir des exemples d’événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consultez <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="095fa-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="095fa-108">Types et événements</span><span class="sxs-lookup"><span data-stu-id="095fa-108">Types and Events</span></span>  
 <span data-ttu-id="095fa-109">Vous utilisez les types suivants lorsque vous travaillez avec des événements :</span><span class="sxs-lookup"><span data-stu-id="095fa-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="095fa-110">Type</span><span class="sxs-lookup"><span data-stu-id="095fa-110">Type</span></span>|<span data-ttu-id="095fa-111">Description</span><span class="sxs-lookup"><span data-stu-id="095fa-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="095fa-112">Spécifie le type d'événement lorsqu'un événement est déclenché pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="095fa-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="095fa-113">Fournit des données pour les événements <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="095fa-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="095fa-114">Les événements suivants sont déclenchés lorsque vous modifiez une arborescence XML :</span><span class="sxs-lookup"><span data-stu-id="095fa-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="095fa-115">Événement</span><span class="sxs-lookup"><span data-stu-id="095fa-115">Event</span></span>|<span data-ttu-id="095fa-116">Description</span><span class="sxs-lookup"><span data-stu-id="095fa-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="095fa-117">Se produit juste avant que cet objet <xref:System.Xml.Linq.XObject> ou l'un de ses descendants ne change.</span><span class="sxs-lookup"><span data-stu-id="095fa-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="095fa-118">Se produit lorsqu'un objet <xref:System.Xml.Linq.XObject> ou l'un des ses descendants a changé.</span><span class="sxs-lookup"><span data-stu-id="095fa-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="095fa-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="095fa-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="095fa-120">Description</span><span class="sxs-lookup"><span data-stu-id="095fa-120">Description</span></span>  
 <span data-ttu-id="095fa-121">Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="095fa-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="095fa-122">Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture.</span><span class="sxs-lookup"><span data-stu-id="095fa-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="095fa-123">Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.</span><span class="sxs-lookup"><span data-stu-id="095fa-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="095fa-124">Code</span><span class="sxs-lookup"><span data-stu-id="095fa-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="095fa-125">Commentaires</span><span class="sxs-lookup"><span data-stu-id="095fa-125">Comments</span></span>  
 <span data-ttu-id="095fa-126">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="095fa-126">This code produces the following output:</span></span>  
  
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
  