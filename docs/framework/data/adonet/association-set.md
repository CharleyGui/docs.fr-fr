---
title: jeu d'associations
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 58d8794a21cc37ab84386c820b192fb29946095c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153428"
---
# <a name="association-set"></a><span data-ttu-id="ac74c-102">jeu d'associations</span><span class="sxs-lookup"><span data-stu-id="ac74c-102">association set</span></span>

<span data-ttu-id="ac74c-103">Un *ensemble d’associations* est un conteneur logique pour les instances d' [Association](association-type.md) du même type.</span><span class="sxs-lookup"><span data-stu-id="ac74c-103">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="ac74c-104">Un ensemble d'associations n'est pas une construction de modélisation des données ; autrement dit, il ne décrit ni la structure de données ni les relations.</span><span class="sxs-lookup"><span data-stu-id="ac74c-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="ac74c-105">Au lieu de cela, un ensemble d'associations fournit une construction pour un environnement d'hébergement ou de stockage (tel que le Common Language Runtime ou une base de données SQL Server) pour regrouper des instances d'association afin qu'elles puissent être mappées à un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="ac74c-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="ac74c-106">Un ensemble d’associations est défini dans un [conteneur d’entités](entity-container.md), qui est un regroupement logique de jeux d' [entités](entity-set.md) et d’ensembles d’associations.</span><span class="sxs-lookup"><span data-stu-id="ac74c-106">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="ac74c-107">Une définition d'ensemble d'associations contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ac74c-107">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="ac74c-108">Nom de l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="ac74c-108">The association set name.</span></span> <span data-ttu-id="ac74c-109">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="ac74c-109">(Required)</span></span>  
  
- <span data-ttu-id="ac74c-110">Association dont l'ensemble d'associations contient des instances.</span><span class="sxs-lookup"><span data-stu-id="ac74c-110">The association of which it will contain instances.</span></span> <span data-ttu-id="ac74c-111">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="ac74c-111">(Required)</span></span>  
  
- <span data-ttu-id="ac74c-112">Deux [terminaisons d’ensemble d’associations](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="ac74c-112">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac74c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac74c-113">Example</span></span>  

 <span data-ttu-id="ac74c-114">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="ac74c-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="ac74c-115">Bien que les informations sur les ensembles d'associations ne soient pas transmises au diagramme, le diagramme suivant montre un exemple d'ensembles d'associations et de jeux d'entités basés sur ce modèle.</span><span class="sxs-lookup"><span data-stu-id="ac74c-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ac74c-117">L'exemple suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) basés sur le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ac74c-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="ac74c-118">Bi dans le `Books` jeu d’entités représente une instance du `Book` type d’entité au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac74c-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="ac74c-119">De même, PJ représente une `Publisher` instance dans le `Publishers` jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="ac74c-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="ac74c-120">BiPj représente une instance de l' `PublishedBy` Association dans l' `PublishedBy` ensemble d’associations.</span><span class="sxs-lookup"><span data-stu-id="ac74c-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Capture d’écran montrant un exemple de jeu.](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="ac74c-122">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="ac74c-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="ac74c-123">Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ac74c-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="ac74c-124">Notez que le nom et l'association pour chaque ensemble d'associations sont définis à l'aide d'attributs XML.</span><span class="sxs-lookup"><span data-stu-id="ac74c-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="ac74c-125">Il est possible de définir plusieurs ensembles d’associations par Association, tant que deux ensembles d’associations ne partagent pas une [terminaison d’ensemble d’associations](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="ac74c-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="ac74c-126">Le CSDL suivant définit un conteneur d'entités avec deux ensembles d'associations pour l'association `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="ac74c-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="ac74c-127">Notez que plusieurs jeux d'entités ont été définis pour les types d'entité `Book` et `Author`, et qu'aucun ensemble d'associations ne partage une terminaison d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="ac74c-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="ac74c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac74c-128">See also</span></span>

- [<span data-ttu-id="ac74c-129">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ac74c-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="ac74c-130">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ac74c-130">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="ac74c-131">Propriété de clé étrangère</span><span class="sxs-lookup"><span data-stu-id="ac74c-131">foreign key property</span></span>](foreign-key-property.md)
