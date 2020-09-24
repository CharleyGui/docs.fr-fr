---
title: multiplicité de terminaison d'association
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153506"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="b9413-102">multiplicité de terminaison d'association</span><span class="sxs-lookup"><span data-stu-id="b9413-102">association end multiplicity</span></span>

<span data-ttu-id="b9413-103">La *multiplicité de terminaison d’association* définit le nombre d’instances de type d' [entité](entity-type.md) qui peuvent être à une terminaison d’une [Association](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="b9413-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="b9413-104">La multiplicité de terminaison d'association peut avoir l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9413-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="b9413-105">Un (1) : indique qu'il existe exactement une instance de type d'entité au niveau de la terminaison d'association.</span><span class="sxs-lookup"><span data-stu-id="b9413-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="b9413-106">Zéro ou un (0..1) : indique qu'il existe zéro ou une instance de type d'entité au niveau de la terminaison d'association.</span><span class="sxs-lookup"><span data-stu-id="b9413-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="b9413-107">Many ( \* ) : indique qu’il existe zéro, une ou plusieurs instances de type d’entité au niveau de la terminaison d’association.</span><span class="sxs-lookup"><span data-stu-id="b9413-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="b9413-108">Une association est souvent caractérisée par ses multiplicités de terminaison d'association.</span><span class="sxs-lookup"><span data-stu-id="b9413-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="b9413-109">Par exemple, si les terminaisons d’une association ont des multiplicités un (1) et plusieurs ( \* ), l’Association est appelée Association un-à-plusieurs.</span><span class="sxs-lookup"><span data-stu-id="b9413-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="b9413-110">Dans l'exemple ci-dessous, l'association `PublishedBy` est une association un-à-plusieurs (un éditeur publie de nombreux livres, et un livre est publié par un seul éditeur).</span><span class="sxs-lookup"><span data-stu-id="b9413-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="b9413-111">L'association `WrittenBy` est une association plusieurs-à-plusieurs (un livre peut avoir plusieurs auteurs, et un auteur peut écrire plusieurs livres).</span><span class="sxs-lookup"><span data-stu-id="b9413-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9413-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9413-112">Example</span></span>  

 <span data-ttu-id="b9413-113">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="b9413-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="b9413-114">Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="b9413-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="b9413-115">La multiplicité de la `Publisher` terminaison est un (1) et la multiplicité de la `Book` terminaison est plusieurs ( \* ).</span><span class="sxs-lookup"><span data-stu-id="b9413-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="b9413-117">Le Entity Framework ADO.NET utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="b9413-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="b9413-118">Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="b9413-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b9413-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9413-119">See also</span></span>

- [<span data-ttu-id="b9413-120">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b9413-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="b9413-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b9413-121">Entity Data Model</span></span>](entity-data-model.md)
