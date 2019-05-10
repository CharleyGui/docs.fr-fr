---
title: multiplicité de terminaison d'association
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: e889394dc28bfe1352bd4c8497d5a74919279fe7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592629"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="72918-102">multiplicité de terminaison d'association</span><span class="sxs-lookup"><span data-stu-id="72918-102">association end multiplicity</span></span>
<span data-ttu-id="72918-103">*Multiplicité de terminaison d’association* définit le nombre de [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) instances qui peuvent être à l’extrémité d’une [association](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="72918-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="72918-104">La multiplicité de terminaison d'association peut avoir l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="72918-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="72918-105">un (1) : Indique que cette instance de type exactement une entité existe à la fin de l’association.</span><span class="sxs-lookup"><span data-stu-id="72918-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="72918-106">zéro ou une (valeur 0.. 1) : Indique que zéro ou une instance de type d’entité existe au niveau de la terminaison d’association.</span><span class="sxs-lookup"><span data-stu-id="72918-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="72918-107">nombre (\*) : Indique que zéro, une ou plusieurs instances de type d’entité existent à la fin de l’association.</span><span class="sxs-lookup"><span data-stu-id="72918-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="72918-108">Une association est souvent caractérisée par ses multiplicités de terminaison d'association.</span><span class="sxs-lookup"><span data-stu-id="72918-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="72918-109">Par exemple, si les terminaisons d’une association ont les multiplicités un (1) et plusieurs (\*), l’association est appelée une association un-à-plusieurs.</span><span class="sxs-lookup"><span data-stu-id="72918-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="72918-110">Dans l'exemple ci-dessous, l'association `PublishedBy` est une association un-à-plusieurs (un éditeur publie de nombreux livres, et un livre est publié par un seul éditeur).</span><span class="sxs-lookup"><span data-stu-id="72918-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="72918-111">L'association `WrittenBy` est une association plusieurs-à-plusieurs (un livre peut avoir plusieurs auteurs, et un auteur peut écrire plusieurs livres).</span><span class="sxs-lookup"><span data-stu-id="72918-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72918-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="72918-112">Example</span></span>  
 <span data-ttu-id="72918-113">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="72918-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="72918-114">Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="72918-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="72918-115">La multiplicité de la `Publisher` fin est un (1) et la multiplicité de la `Book` fin est plusieurs (\*).</span><span class="sxs-lookup"><span data-stu-id="72918-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="72918-117">ADO.NET Entity Framework utilise un langage spécifique à un domaine (DSL) appelé langage de définition de schéma conceptuel ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="72918-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="72918-118">Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="72918-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="72918-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72918-119">See also</span></span>

- [<span data-ttu-id="72918-120">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="72918-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="72918-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="72918-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
