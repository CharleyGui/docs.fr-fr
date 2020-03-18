---
title: 'Exemple de fichier XML : Données numériques dans un espace de noms3'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 02788b73a7af9922b5a50237f2d2e401cba8abe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483703"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="ffb4e-102">Exemple de fichier XML : Données numériques dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="ffb4e-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="ffb4e-103">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffb4e-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="ffb4e-104">Ce fichier contient des données numériques pour effectuer des additions, des moyennes et des regroupements.</span><span class="sxs-lookup"><span data-stu-id="ffb4e-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="ffb4e-105">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ffb4e-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="ffb4e-106">Données</span><span class="sxs-lookup"><span data-stu-id="ffb4e-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
