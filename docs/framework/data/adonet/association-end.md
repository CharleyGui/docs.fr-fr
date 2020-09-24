---
title: terminaison d'association
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 00e3a7d855957ae539ea652dc8cde3ed8841dda5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153441"
---
# <a name="association-end"></a><span data-ttu-id="91f5c-102">terminaison d'association</span><span class="sxs-lookup"><span data-stu-id="91f5c-102">association end</span></span>

<span data-ttu-id="91f5c-103">Une *terminaison d’association* identifie le [type d’entité](entity-type.md) sur une terminaison d’une [Association](association-type.md) et le nombre d’instances de type d’entité qui peuvent exister à cette terminaison d’une association.</span><span class="sxs-lookup"><span data-stu-id="91f5c-103">An *association end* identifies the [entity type](entity-type.md) on one end of an [association](association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="91f5c-104">Les terminaisons d'association sont définies dans le cadre d'une association ; une association doit avoir exactement deux terminaisons d'association.</span><span class="sxs-lookup"><span data-stu-id="91f5c-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="91f5c-105">Les [Propriétés de navigation](navigation-property.md) permettent de naviguer d’une terminaison d’association à l’autre.</span><span class="sxs-lookup"><span data-stu-id="91f5c-105">[Navigation properties](navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="91f5c-106">Une définition de terminaison d'association contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="91f5c-106">An association end definition contains the following information:</span></span>  
  
- <span data-ttu-id="91f5c-107">Un des types d'entité impliqués dans l'association.</span><span class="sxs-lookup"><span data-stu-id="91f5c-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="91f5c-108">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="91f5c-108">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91f5c-109">Pour une association donnée, le type d'entité spécifié pour chaque terminaison d'association peut être le même.</span><span class="sxs-lookup"><span data-stu-id="91f5c-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="91f5c-110">Ceci crée une association automatique.</span><span class="sxs-lookup"><span data-stu-id="91f5c-110">This creates a self-association.</span></span>  
  
- <span data-ttu-id="91f5c-111">[Multiplicité de terminaison d’association](association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à une terminaison de l’Association.</span><span class="sxs-lookup"><span data-stu-id="91f5c-111">An [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="91f5c-112">Une multiplicité de terminaison d’association peut avoir la valeur un (1), zéro ou un (0.. 1), ou plusieurs ( \* ).</span><span class="sxs-lookup"><span data-stu-id="91f5c-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
- <span data-ttu-id="91f5c-113">Nom de la terminaison de l'association.</span><span class="sxs-lookup"><span data-stu-id="91f5c-113">A name for the association end.</span></span> <span data-ttu-id="91f5c-114">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="91f5c-114">(Optional)</span></span>  
  
- <span data-ttu-id="91f5c-115">Informations sur les opérations effectuées sur la terminaison d'association, telles que CASCADE sur DELETE.</span><span class="sxs-lookup"><span data-stu-id="91f5c-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="91f5c-116">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="91f5c-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="91f5c-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="91f5c-117">Example</span></span>  

 <span data-ttu-id="91f5c-118">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="91f5c-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="91f5c-119">Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="91f5c-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="91f5c-120">La multiplicité de la `Publisher` terminaison est un (1) et la multiplicité de la `Book` terminaison est plusieurs ( \* ), ce qui indique qu’un éditeur publie de nombreux livres et qu’un livre est publié par un serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="91f5c-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="91f5c-122">Le Entity Framework ADO.NET utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="91f5c-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="91f5c-123">Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="91f5c-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="91f5c-124">Notez que le type, le nom et la multiplicité de chaque terminaison d'association sont spécifiés par des attributs XML (`Type`, `Role` et `Multiplicity`, respectivement).</span><span class="sxs-lookup"><span data-stu-id="91f5c-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="91f5c-125">Des informations facultatives sur les opérations effectuées sur une terminaison sont spécifiées dans un élément XML (`OnDelete`).</span><span class="sxs-lookup"><span data-stu-id="91f5c-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="91f5c-126">Dans ce cas, si un éditeur est supprimé, tous les livres associés le sont aussi.</span><span class="sxs-lookup"><span data-stu-id="91f5c-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="91f5c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91f5c-127">See also</span></span>

- [<span data-ttu-id="91f5c-128">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="91f5c-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="91f5c-129">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="91f5c-129">Entity Data Model</span></span>](entity-data-model.md)
