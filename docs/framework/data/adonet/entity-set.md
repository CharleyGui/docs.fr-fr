---
title: jeu d'entités
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 6286d3707a8506e7a389359a5aa361c152e75212
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194790"
---
# <a name="entity-set"></a><span data-ttu-id="7d848-102">jeu d'entités</span><span class="sxs-lookup"><span data-stu-id="7d848-102">entity set</span></span>

<span data-ttu-id="7d848-103">Un *jeu d’entités* est un conteneur logique pour les instances d’un [type d’entité](entity-type.md) et les instances de tout type dérivé de ce type d’entité.</span><span class="sxs-lookup"><span data-stu-id="7d848-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="7d848-104">(Pour plus d’informations sur les types dérivés, consultez [Entity Data Model : héritage](entity-data-model-inheritance.md)). La relation entre un type d’entité et un jeu d’entités est analogue à la relation entre une ligne et une table dans une base de données relationnelle : comme une ligne, un type d’entité décrit la structure des données et, comme une table, un jeu d’entités contient des instances d’une structure donnée.</span><span class="sxs-lookup"><span data-stu-id="7d848-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="7d848-105">Un jeu d'entités n'est pas une construction de modélisation des données ; il ne décrit pas la structure des données.</span><span class="sxs-lookup"><span data-stu-id="7d848-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="7d848-106">Au lieu de cela, un jeu d'entités fournit une construction pour un environnement d'hébergement ou de stockage (tel que le Common Language Runtime ou une base de données SQL Server) pour regrouper des instances de type d'entité afin qu'elles puissent être mappées à une banque de données.</span><span class="sxs-lookup"><span data-stu-id="7d848-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="7d848-107">Un jeu d’entités est défini dans un [conteneur d’entités](entity-container.md), qui est un regroupement logique de jeux d’entités et d’ensembles d' [associations](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="7d848-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="7d848-108">Pour qu'une instance de type d'entité existe dans un jeu d'entités, les conditions suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="7d848-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="7d848-109">Le type de l'instance est soit le même que le type d'entité sur lequel le jeu d'entités est basé, soit un sous-type du type d'entité.</span><span class="sxs-lookup"><span data-stu-id="7d848-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="7d848-110">La [clé d’entité](entity-key.md) de l’instance est unique dans le jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="7d848-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="7d848-111">L'instance n'existe dans aucun autre jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="7d848-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7d848-112">Plusieurs jeux d'entités peuvent être définis à l'aide du même type d'entité, mais une instance d'un type d'entité donné ne peut exister que dans un seul jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="7d848-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="7d848-113">Il n'est pas nécessaire de définir un jeu d'entités pour chaque type d'entité dans un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="7d848-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d848-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d848-114">Example</span></span>  

 <span data-ttu-id="7d848-115">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="7d848-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="7d848-117">Le diagramme suivant montre deux jeux d'entités (`Books` et `Publishers`) et un ensemble d'associations (`PublishedBy`) selon le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7d848-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="7d848-118">Bi dans le `Books` jeu d’entités représente une instance du `Book` type d’entité au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d848-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="7d848-119">De même, PJ représente une `Publisher` instance dans le `Publishers` jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="7d848-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="7d848-120">BiPj représente une instance de l' `PublishedBy` Association dans l' `PublishedBy` ensemble d’associations.</span><span class="sxs-lookup"><span data-stu-id="7d848-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Capture d’écran montrant un exemple de jeu.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="7d848-122">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="7d848-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7d848-123">Le CSDL suivant définit un conteneur d'entités avec un jeu d'entités pour chaque type d'entité dans le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7d848-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="7d848-124">Notez que le nom et le type d'entité pour chaque jeu d'entités sont définis à l'aide d'attributs XML.</span><span class="sxs-lookup"><span data-stu-id="7d848-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="7d848-125">Il est possible de définir des jeux d'entités multiples par type (MEST).</span><span class="sxs-lookup"><span data-stu-id="7d848-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="7d848-126">Le CSDL suivant définit un conteneur d'entités avec deux jeux d'entités pour le type d'entité `Book` :</span><span class="sxs-lookup"><span data-stu-id="7d848-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7d848-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d848-127">See also</span></span>

- [<span data-ttu-id="7d848-128">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="7d848-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7d848-129">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="7d848-129">Entity Data Model</span></span>](entity-data-model.md)
