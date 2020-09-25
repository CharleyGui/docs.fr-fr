---
title: contrainte d'intégrité référentielle
description: Découvrez les contraintes d’intégrité référentielle dans le Entity Data Model, qui garantissent que les associations valides existent toujours entre les types d’entités.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 6ade9d0155a6915757c7f47c5cb3ab0a51dbd437
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172734"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="9d310-103">contrainte d'intégrité référentielle</span><span class="sxs-lookup"><span data-stu-id="9d310-103">referential integrity constraint</span></span>

<span data-ttu-id="9d310-104">Une *contrainte d’intégrité référentielle* dans le Entity Data Model (EDM) est similaire à une contrainte d’intégrité référentielle dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="9d310-104">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="9d310-105">De la même façon qu’une colonne (ou des colonnes) d’une table de base de données peut faire référence à la clé primaire d’une autre table [, une ou plusieurs propriétés d'](property.md) un [type d’entité](entity-type.md) peuvent référencer la [clé d’entité](entity-key.md) d’un autre type d’entité.</span><span class="sxs-lookup"><span data-stu-id="9d310-105">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="9d310-106">Le type d’entité référencé est appelé *terminaison principale* de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9d310-106">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="9d310-107">Le type d’entité qui référence la terminaison principale est appelé *terminaison dépendante* de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9d310-107">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="9d310-108">Une contrainte d’intégrité référentielle est définie dans le cadre d’une [Association](association-type.md) entre deux types d’entités.</span><span class="sxs-lookup"><span data-stu-id="9d310-108">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="9d310-109">La définition d'une contrainte d'intégrité référentielle spécifie les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d310-109">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="9d310-110">Terminaison principale de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9d310-110">The principal end of the constraint.</span></span> <span data-ttu-id="9d310-111">(Type d'entité dont la clé d'entité est référencée par la terminaison dépendante.)</span><span class="sxs-lookup"><span data-stu-id="9d310-111">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="9d310-112">Clé d'entité de la terminaison principale.</span><span class="sxs-lookup"><span data-stu-id="9d310-112">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="9d310-113">Terminaison dépendante de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9d310-113">The dependent end of the constraint.</span></span> <span data-ttu-id="9d310-114">(Type d'entité dont une ou plusieurs propriétés référencent la clé d'entité de la terminaison principale.)</span><span class="sxs-lookup"><span data-stu-id="9d310-114">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="9d310-115">Propriété ou propriétés de référence de la terminaison dépendante.</span><span class="sxs-lookup"><span data-stu-id="9d310-115">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="9d310-116">Les contraintes d'intégrité référentielle dans le modèle EDM ont pour objectif de vérifier que des associations valides existent toujours.</span><span class="sxs-lookup"><span data-stu-id="9d310-116">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="9d310-117">Pour plus d’informations, consultez [propriété de clé étrangère](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="9d310-117">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d310-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d310-118">Example</span></span>  

 <span data-ttu-id="9d310-119">Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="9d310-119">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="9d310-120">Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="9d310-120">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="9d310-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Exemple de modèle de contrainte référentielle")</span><span class="sxs-lookup"><span data-stu-id="9d310-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="9d310-122">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="9d310-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="9d310-123">Le CSDL suivant définit une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9d310-123">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="9d310-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d310-124">See also</span></span>

- [<span data-ttu-id="9d310-125">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="9d310-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="9d310-126">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="9d310-126">Entity Data Model</span></span>](entity-data-model.md)
