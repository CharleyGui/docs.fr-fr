---
title: Limitations des inférences
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 9d8191be137661200e1a6b84d68328c1202880ca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172773"
---
# <a name="inference-limitations"></a><span data-ttu-id="a95d4-102">Limitations des inférences</span><span class="sxs-lookup"><span data-stu-id="a95d4-102">Inference Limitations</span></span>

<span data-ttu-id="a95d4-103">Le processus d'inférence d'un schéma de l'objet <xref:System.Data.DataSet> à partir de XML peut aboutir à des schémas différents en fonction des éléments XML figurant dans chaque document.</span><span class="sxs-lookup"><span data-stu-id="a95d4-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="a95d4-104">Examinons, par exemple, les documents XML suivants.</span><span class="sxs-lookup"><span data-stu-id="a95d4-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="a95d4-105">Document1 :</span><span class="sxs-lookup"><span data-stu-id="a95d4-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a95d4-106">Document2 :</span><span class="sxs-lookup"><span data-stu-id="a95d4-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a95d4-107">Pour « Document1 », le processus d’inférence produit un **DataSet** nommé « DocumentElement » et une table nommée « Element1 », car « Element1 » est un élément répétitif.</span><span class="sxs-lookup"><span data-stu-id="a95d4-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="a95d4-108">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a95d4-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a95d4-109">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="a95d4-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a95d4-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a95d4-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="a95d4-111">Text1</span><span class="sxs-lookup"><span data-stu-id="a95d4-111">Text1</span></span>|  
|<span data-ttu-id="a95d4-112">Text2</span><span class="sxs-lookup"><span data-stu-id="a95d4-112">Text2</span></span>|  
  
 <span data-ttu-id="a95d4-113">Toutefois, pour « document2 », le processus d’inférence produit un **jeu de données** nommé « NewDataSet » et une table nommée « documentElement ».</span><span class="sxs-lookup"><span data-stu-id="a95d4-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="a95d4-114">« Element1 » est déduit en tant que colonne car il n'a ni attribut, ni élément enfant.</span><span class="sxs-lookup"><span data-stu-id="a95d4-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="a95d4-115">**Jeu de données :** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="a95d4-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="a95d4-116">**Table :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a95d4-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="a95d4-117">Element1</span><span class="sxs-lookup"><span data-stu-id="a95d4-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="a95d4-118">Text1</span><span class="sxs-lookup"><span data-stu-id="a95d4-118">Text1</span></span>|  
  
 <span data-ttu-id="a95d4-119">Ces deux documents XML peuvent avoir été conçus de manière à produire le même schéma, mais le processus d'inférence donne des résultats très différents en fonction des éléments contenus dans chaque document.</span><span class="sxs-lookup"><span data-stu-id="a95d4-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="a95d4-120">Pour éviter les incohérences qui peuvent se produire lors de la génération d’un schéma à partir d’un document XML, nous vous recommandons de spécifier explicitement un schéma à l’aide du langage XSD (XML Schema Definition) ou XDR (XML-Data Reduced) lors du chargement d’un **DataSet** à partir de XML.</span><span class="sxs-lookup"><span data-stu-id="a95d4-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="a95d4-121">Pour plus d’informations sur la spécification explicite d’un schéma de **DataSet** à l’aide d’un schéma XML, consultez [dérivation de la structure relationnelle d’un DataSet à partir d’un schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="a95d4-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a95d4-122">See also</span></span>

- [<span data-ttu-id="a95d4-123">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a95d4-123">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="a95d4-124">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a95d4-124">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="a95d4-125">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a95d4-125">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="a95d4-126">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="a95d4-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a95d4-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a95d4-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a95d4-128">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a95d4-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
