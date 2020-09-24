---
title: Déduction du texte d'un élément
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 7389e24f39902edf041c3cd3502303b17fd008ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164686"
---
# <a name="inferring-element-text"></a><span data-ttu-id="d1fe7-102">Déduction du texte d'un élément</span><span class="sxs-lookup"><span data-stu-id="d1fe7-102">Inferring Element Text</span></span>

<span data-ttu-id="d1fe7-103">Si un élément contient du texte et qu’il n’a pas d’éléments enfants à déduire en tant que tables (comme des éléments avec des attributs ou des éléments répétés), une nouvelle colonne portant le nom **TableName_Text** sera ajoutée à la table déduite pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="d1fe7-104">Le texte contenu dans l'élément sera ajouté à une ligne de la table et stocké dans la nouvelle colonne.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="d1fe7-105">La propriété **ColumnMapping** de la nouvelle colonne sera définie sur **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="d1fe7-106">Examinons, par exemple, le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d1fe7-107">Le processus d’inférence produira une table nommée **element1** avec deux colonnes : **attr1** et **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="d1fe7-108">La propriété **ColumnMapping** de la colonne **attr1** aura pour valeur **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="d1fe7-109">La propriété **ColumnMapping** de la colonne **Element1_Text** sera définie sur **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="d1fe7-110">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d1fe7-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d1fe7-111">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d1fe7-112">attr1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-112">attr1</span></span>|<span data-ttu-id="d1fe7-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d1fe7-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="d1fe7-114">valeur1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-114">value1</span></span>|<span data-ttu-id="d1fe7-115">Text1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-115">Text1</span></span>|  
  
 <span data-ttu-id="d1fe7-116">Si un élément contient du texte, mais possède également des éléments enfants contenant du texte, une colonne ne sera pas ajoutée à la table pour stocker le texte contenu dans l'élément.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="d1fe7-117">Ce texte sera ignoré, alors que le texte des éléments enfants sera inclus dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="d1fe7-118">Examinons, par exemple, le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="d1fe7-119">Le processus d’inférence produira une table nommée **element1** avec une colonne nommée **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="d1fe7-120">Le texte de l’élément **ChildElement1** sera inclus dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="d1fe7-121">L'autre texte sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-121">The other text will be ignored.</span></span> <span data-ttu-id="d1fe7-122">La propriété **ColumnMapping** de la colonne **ChildElement1** sera définie sur **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="d1fe7-123">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d1fe7-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d1fe7-124">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d1fe7-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="d1fe7-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="d1fe7-126">Text2</span><span class="sxs-lookup"><span data-stu-id="d1fe7-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1fe7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1fe7-127">See also</span></span>

- [<span data-ttu-id="d1fe7-128">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="d1fe7-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="d1fe7-129">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="d1fe7-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="d1fe7-130">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="d1fe7-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="d1fe7-131">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="d1fe7-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="d1fe7-132">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="d1fe7-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d1fe7-133">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1fe7-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
