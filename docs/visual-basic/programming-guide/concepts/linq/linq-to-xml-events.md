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
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="6ef39-102">Événements de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ef39-102">LINQ to XML Events (Visual Basic)</span></span>
<span data-ttu-id="6ef39-103">Les événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’être averti quand une arborescence XML est modifiée.</span><span class="sxs-lookup"><span data-stu-id="6ef39-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="6ef39-104">Vous pouvez ajouter des événements à une instance de n'importe quel objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6ef39-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="6ef39-105">Le gestionnaire d'événements recevra alors des événements en cas de modification apportée à cet objet <xref:System.Xml.Linq.XObject> et à l'un de ses descendants.</span><span class="sxs-lookup"><span data-stu-id="6ef39-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="6ef39-106">Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="6ef39-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="6ef39-107">Pour obtenir des exemples d’événements [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consultez <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="6ef39-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="6ef39-108">Types et événements</span><span class="sxs-lookup"><span data-stu-id="6ef39-108">Types and Events</span></span>  
 <span data-ttu-id="6ef39-109">Vous utilisez les types suivants lorsque vous travaillez avec des événements :</span><span class="sxs-lookup"><span data-stu-id="6ef39-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="6ef39-110">Type</span><span class="sxs-lookup"><span data-stu-id="6ef39-110">Type</span></span>|<span data-ttu-id="6ef39-111">Description</span><span class="sxs-lookup"><span data-stu-id="6ef39-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="6ef39-112">Spécifie le type d'événement lorsqu'un événement est déclenché pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6ef39-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="6ef39-113">Fournit des données pour les événements <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="6ef39-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="6ef39-114">Les événements suivants sont déclenchés lorsque vous modifiez une arborescence XML :</span><span class="sxs-lookup"><span data-stu-id="6ef39-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="6ef39-115">Événement</span><span class="sxs-lookup"><span data-stu-id="6ef39-115">Event</span></span>|<span data-ttu-id="6ef39-116">Description</span><span class="sxs-lookup"><span data-stu-id="6ef39-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="6ef39-117">Se produit juste avant que cet objet <xref:System.Xml.Linq.XObject> ou l'un de ses descendants ne change.</span><span class="sxs-lookup"><span data-stu-id="6ef39-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="6ef39-118">Se produit lorsqu'un objet <xref:System.Xml.Linq.XObject> ou l'un des ses descendants a changé.</span><span class="sxs-lookup"><span data-stu-id="6ef39-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ef39-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ef39-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6ef39-120">Description</span><span class="sxs-lookup"><span data-stu-id="6ef39-120">Description</span></span>  
 <span data-ttu-id="6ef39-121">Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6ef39-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="6ef39-122">Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture.</span><span class="sxs-lookup"><span data-stu-id="6ef39-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="6ef39-123">Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.</span><span class="sxs-lookup"><span data-stu-id="6ef39-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6ef39-124">Code</span><span class="sxs-lookup"><span data-stu-id="6ef39-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6ef39-125">Commentaires</span><span class="sxs-lookup"><span data-stu-id="6ef39-125">Comments</span></span>  
 <span data-ttu-id="6ef39-126">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6ef39-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ef39-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ef39-127">See also</span></span>

- [<span data-ttu-id="6ef39-128">Visual Basic (Advanced LINQ to XML Programming)</span><span class="sxs-lookup"><span data-stu-id="6ef39-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
