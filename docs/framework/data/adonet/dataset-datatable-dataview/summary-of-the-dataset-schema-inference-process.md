---
title: Résumé du processus d'inférence du schéma de données
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198507"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="9839a-102">Résumé du processus d'inférence du schéma de données</span><span class="sxs-lookup"><span data-stu-id="9839a-102">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="9839a-103">Le processus d'inférence identifie d'abord, à partir du document XML, les éléments qui seront déduits en tant que tables.</span><span class="sxs-lookup"><span data-stu-id="9839a-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="9839a-104">À partir du XML restant, le processus d'inférence détermine les colonnes qui feront partie de ces tables.</span><span class="sxs-lookup"><span data-stu-id="9839a-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="9839a-105">Pour les tables imbriquées, le processus d'inférence génère des objets <xref:System.Data.DataRelation> et <xref:System.Data.ForeignKeyConstraint> imbriqués.</span><span class="sxs-lookup"><span data-stu-id="9839a-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="9839a-106">Voici un bref résumé des règles d’inférence :</span><span class="sxs-lookup"><span data-stu-id="9839a-106">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="9839a-107">Les éléments assortis d'attributs sont déduits en tant que tables.</span><span class="sxs-lookup"><span data-stu-id="9839a-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="9839a-108">Les éléments possédant des éléments enfants sont déduits en tant que tables.</span><span class="sxs-lookup"><span data-stu-id="9839a-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="9839a-109">Les éléments qui se répètent sont déduits une seule fois en tant que table.</span><span class="sxs-lookup"><span data-stu-id="9839a-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="9839a-110">Si l'élément de document, ou racine, ne comporte pas d'attributs ni d'éléments enfants qui seraient déduits en tant que colonnes, il est déduit en tant qu'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9839a-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9839a-111">Sinon, l'élément de document est déduit en tant que table.</span><span class="sxs-lookup"><span data-stu-id="9839a-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="9839a-112">Les attributs sont déduits en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="9839a-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="9839a-113">Les éléments dépourvus d'attributs ou d'éléments enfants et qui ne se répètent pas sont déduits en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="9839a-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="9839a-114">Pour les éléments qui sont déduits en tant que tables imbriquées dans d’autres éléments également déduits en tant que tables, un **DataRelation** imbriqué est créé entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="9839a-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="9839a-115">Une nouvelle colonne de clé primaire nommée **TableName_Id** est ajoutée aux deux tables et utilisée par le **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="9839a-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="9839a-116">Un **ForeignKeyConstraint** est créé entre les deux tables à l’aide de la **TableName_Id** colonne.</span><span class="sxs-lookup"><span data-stu-id="9839a-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="9839a-117">Pour les éléments qui sont déduits en tant que tables et qui contiennent du texte mais n’ont pas d’éléments enfants, une nouvelle colonne nommée **TableName_Text** est créée pour le texte de chacun des éléments.</span><span class="sxs-lookup"><span data-stu-id="9839a-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="9839a-118">Si un élément déduit en tant que table comprend du texte, mais également des éléments enfants, le texte est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9839a-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9839a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9839a-119">See also</span></span>

- [<span data-ttu-id="9839a-120">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9839a-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="9839a-121">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9839a-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="9839a-122">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9839a-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="9839a-123">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="9839a-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="9839a-124">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="9839a-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9839a-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9839a-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
