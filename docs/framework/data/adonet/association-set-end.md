---
title: terminaison d'ensemble d'associations
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: f7ec1ca6fcdf299b9fcfc78f299ea4c6c5267cd3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738620"
---
# <a name="association-set-end"></a><span data-ttu-id="34157-102">terminaison d'ensemble d'associations</span><span class="sxs-lookup"><span data-stu-id="34157-102">association set end</span></span>
<span data-ttu-id="34157-103">Une *terminaison d’ensemble d’associations* identifie le [type d’entité](entity-type.md) et le [jeu d’entités](entity-set.md) à la fin d’un [ensemble d’associations](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="34157-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="34157-104">Les terminaisons d'ensemble d'associations sont définies dans le cadre d'un ensemble d'associations ; un ensemble d'associations doit avoir exactement deux terminaisons d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="34157-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="34157-105">Une définition de terminaison d'ensemble d'associations contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="34157-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="34157-106">Un des types d'entité impliqués dans l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="34157-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="34157-107">(Requis)</span><span class="sxs-lookup"><span data-stu-id="34157-107">(Required)</span></span>  
  
- <span data-ttu-id="34157-108">Jeu d'entités pour le type d'entité impliqué dans l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="34157-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="34157-109">(Requis)</span><span class="sxs-lookup"><span data-stu-id="34157-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="34157-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="34157-110">Example</span></span>  
 <span data-ttu-id="34157-111">Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="34157-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="34157-113">Le diagramme suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) selon le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="34157-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="34157-114">Les terminaisons d'ensemble d'associations sont les jeux d'entités `Books` et `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="34157-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="34157-115">Bi dans le jeu d’entités `Books` représente une instance du type d’entité `Book` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="34157-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="34157-116">De même, PJ représente une instance `Publisher` dans le jeu d’entités `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="34157-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="34157-117">BiPj représente une instance de l’Association `PublishedBy` dans l’ensemble d’associations `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="34157-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Capture d’écran montrant un exemple de jeu.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="34157-119">Le [Entity Framework ADO.net](./ef/index.md) utilise une DSL appelée Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="34157-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="34157-120">Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="34157-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="34157-121">Notez que les terminaisons d'ensemble d'associations sont définies dans le cadre de chaque définition d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="34157-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="34157-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34157-122">See also</span></span>

- [<span data-ttu-id="34157-123">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="34157-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="34157-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="34157-124">Entity Data Model</span></span>](entity-data-model.md)
