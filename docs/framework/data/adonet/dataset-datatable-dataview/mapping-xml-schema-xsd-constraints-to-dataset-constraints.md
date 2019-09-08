---
title: Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786074"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="74b6b-102">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="74b6b-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="74b6b-103">Le langage XSD (XML Schema Definition) permet la spécification de contraintes sur les éléments et attributs qu'il définit.</span><span class="sxs-lookup"><span data-stu-id="74b6b-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="74b6b-104">Lors du mappage d’un schéma XML à un schéma relationnel <xref:System.Data.DataSet>dans un, les contraintes de schéma XML sont mappées à des contraintes relationnelles appropriées sur les tables et les colonnes du **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="74b6b-105">Cette section présente le mappage des contraintes de schéma XML suivantes :</span><span class="sxs-lookup"><span data-stu-id="74b6b-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="74b6b-106">Contrainte d’unicité spécifiée à l’aide de l’élément **unique** .</span><span class="sxs-lookup"><span data-stu-id="74b6b-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="74b6b-107">Contrainte de clé spécifiée à l’aide de l’élément **Key** .</span><span class="sxs-lookup"><span data-stu-id="74b6b-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="74b6b-108">Contrainte keyref spécifiée à l’aide de l’élément **keyref** .</span><span class="sxs-lookup"><span data-stu-id="74b6b-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="74b6b-109">En utilisant une contrainte sur un élément ou un attribut, vous spécifiez certaines restrictions sur les valeurs de l'élément dans toute instance du document.</span><span class="sxs-lookup"><span data-stu-id="74b6b-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="74b6b-110">Par exemple, une contrainte de clé sur un élément enfant **CustomerID** d’un élément **Customer** dans le schéma indique que les valeurs de l’élément enfant **CustomerID** doivent être uniques dans toute instance de document et que les valeurs NULL ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="74b6b-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="74b6b-111">Des contraintes peuvent également être spécifiées entre les éléments et les attributs figurant dans un document afin d'établir une relation dans ce document.</span><span class="sxs-lookup"><span data-stu-id="74b6b-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="74b6b-112">Les contraintes key et keyref sont utilisées dans le schéma pour spécifier les contraintes au sein du document, créant ainsi une relation entre éléments et attributs du document.</span><span class="sxs-lookup"><span data-stu-id="74b6b-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="74b6b-113">Le processus de mappage convertit ces contraintes de schéma en contraintes appropriées sur les tables créées dans le **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74b6b-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="74b6b-114">In This Section</span></span>  
 [<span data-ttu-id="74b6b-115">Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="74b6b-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="74b6b-116">Décrit les éléments de schéma XML utilisés pour créer des contraintes uniques dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="74b6b-117">Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="74b6b-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="74b6b-118">Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé (contraintes uniques où les valeurs NULL ne sont pas autorisées) dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="74b6b-119">Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="74b6b-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="74b6b-120">Décrit les éléments de schéma XML utilisés pour créer des contraintes keyref (clé étrangère) dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="74b6b-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="74b6b-121">Related Sections</span></span>  
 [<span data-ttu-id="74b6b-122">Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="74b6b-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="74b6b-123">Décrit la structure relationnelle, ou schéma, d’un **DataSet** créé à partir du schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="74b6b-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="74b6b-124">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="74b6b-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="74b6b-125">Décrit les éléments de schéma XML utilisés pour créer des relations entre des colonnes de table dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="74b6b-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b6b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74b6b-126">See also</span></span>

- [<span data-ttu-id="74b6b-127">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="74b6b-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
