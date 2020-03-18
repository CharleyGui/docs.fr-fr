---
title: 'Exemple de fichier XML : Commande fournisseur typique dans un espace de noms'
ms.date: 07/20/2015
ms.assetid: 84dc3339-ea32-4ccc-9af6-ab38ddfecced
ms.openlocfilehash: 001a12210c2252d9718425d0d4013bdbdf25b996
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167962"
---
# <a name="sample-xml-file-typical-purchase-order-in-a-namespace"></a><span data-ttu-id="e113d-102">Exemple de fichier XML : Commande fournisseur typique dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="e113d-102">Sample XML File: Typical Purchase Order in a Namespace</span></span>
<span data-ttu-id="e113d-103">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e113d-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="e113d-104">Il concerne une commande fournisseur typique.</span><span class="sxs-lookup"><span data-stu-id="e113d-104">This file is a typical purchase order.</span></span> <span data-ttu-id="e113d-105">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e113d-105">The XML is in a namespace.</span></span>  
  
## <a name="purchaseorderinnamespacexml"></a><span data-ttu-id="e113d-106">PurchaseOrderInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="e113d-106">PurchaseOrderInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<aw:PurchaseOrder  
    aw:PurchaseOrderNumber="99503"  
    aw:OrderDate="1999-10-20"  
    xmlns:aw="http://www.adventure-works.com">  
  <aw:Address aw:Type="Shipping">  
    <aw:Name>Ellen Adams</aw:Name>  
    <aw:Street>123 Maple Street</aw:Street>  
    <aw:City>Mill Valley</aw:City>  
    <aw:State>CA</aw:State>  
    <aw:Zip>10999</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:Address aw:Type="Billing">  
    <aw:Name>Tai Yee</aw:Name>  
    <aw:Street>8 Oak Avenue</aw:Street>  
    <aw:City>Old Town</aw:City>  
    <aw:State>PA</aw:State>  
    <aw:Zip>95819</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:DeliveryNotes>Please leave packages in shed by driveway.</aw:DeliveryNotes>  
  <aw:Items>  
    <aw:Item aw:PartNumber="872-AA">  
      <aw:ProductName>Lawnmower</aw:ProductName>  
      <aw:Quantity>1</aw:Quantity>  
      <aw:USPrice>148.95</aw:USPrice>  
      <aw:Comment>Confirm this is electric</aw:Comment>  
    </aw:Item>  
    <aw:Item aw:PartNumber="926-AA">  
      <aw:ProductName>Baby Monitor</aw:ProductName>  
      <aw:Quantity>2</aw:Quantity>  
      <aw:USPrice>39.98</aw:USPrice>  
      <aw:ShipDate>1999-05-21</aw:ShipDate>  
    </aw:Item>  
  </aw:Items>  
</aw:PurchaseOrder>  
```  
