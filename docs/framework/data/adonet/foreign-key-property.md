---
title: Propriété de clé étrangère
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a77f7479ce38cb34830377021157f312916baca4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738397"
---
# <a name="foreign-key-property"></a><span data-ttu-id="12b2f-102">Propriété de clé étrangère</span><span class="sxs-lookup"><span data-stu-id="12b2f-102">foreign key property</span></span>
<span data-ttu-id="12b2f-103">Une *propriété de clé étrangère* dans le Entity Data Model (EDM) est une [propriété](property.md) de type primitif (ou un ensemble de propriétés de type primitif) sur un [type d’entité](entity-type.md) qui contient la clé d' [entité](entity-key.md) d’un autre type d’entité.</span><span class="sxs-lookup"><span data-stu-id="12b2f-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="12b2f-104">Une propriété de clé étrangère est analogue à une colonne clé étrangère dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="12b2f-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="12b2f-105">De la même façon que les colonnes clés étrangères sont utilisées dans une base de données relationnelle pour créer des relations entre les lignes dans les tables, les propriétés de clé étrangère dans un modèle conceptuel sont utilisées pour établir des [associations](association-type.md) entre les types d’entités.</span><span class="sxs-lookup"><span data-stu-id="12b2f-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="12b2f-106">Une [contrainte d’intégrité référentielle](referential-integrity-constraint.md) est utilisée pour définir une association entre deux types d’entité lorsque l’un des types a une propriété de clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="12b2f-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12b2f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="12b2f-107">Example</span></span>  
 <span data-ttu-id="12b2f-108">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="12b2f-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="12b2f-109">Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="12b2f-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="12b2f-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Exemple de modèle de contrainte référentielle")</span><span class="sxs-lookup"><span data-stu-id="12b2f-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="12b2f-111">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="12b2f-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="12b2f-112">Le CSDL suivant utilise la propriété de clé étrangère `PublisherId` pour définir une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="12b2f-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="12b2f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12b2f-113">See also</span></span>

- [<span data-ttu-id="12b2f-114">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12b2f-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="12b2f-115">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12b2f-115">Entity Data Model</span></span>](entity-data-model.md)
