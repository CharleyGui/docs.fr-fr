---
title: 'Exemple de fichier XML : commande fournisseur typique dans un espace de noms-LINQ to XML'
description: Ce fichier XML, qui est utilisé dans les exemples, contient des données, dans un espace de noms, sur un bon de commande.
ms.date: 07/20/2015
ms.assetid: 84dc3339-ea32-4ccc-9af6-ab38ddfecced
ms.openlocfilehash: 052fbfd680efa863cd5ece386e40350d412285cf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553439"
---
# <a name="sample-xml-file-typical-purchase-order-in-a-namespace-linq-to-xml"></a><span data-ttu-id="8e0dd-103">Exemple de fichier XML : commande fournisseur typique dans un espace de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8e0dd-103">Sample XML file: Typical purchase order in a namespace (LINQ to XML)</span></span>

<span data-ttu-id="8e0dd-104">Le fichier XML suivant est utilisé dans différents exemples de la documentation de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="8e0dd-104">The following XML file is used in various examples in the LINQ to XML documentation.</span></span> <span data-ttu-id="8e0dd-105">Il concerne une commande fournisseur typique.</span><span class="sxs-lookup"><span data-stu-id="8e0dd-105">This file is a typical purchase order.</span></span> <span data-ttu-id="8e0dd-106">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8e0dd-106">The XML is in a namespace.</span></span>

## <a name="purchaseorderinnamespacexml"></a><span data-ttu-id="8e0dd-107">PurchaseOrderInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="8e0dd-107">PurchaseOrderInNamespace.xml</span></span>

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
