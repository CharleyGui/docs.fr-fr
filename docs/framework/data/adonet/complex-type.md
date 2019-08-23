---
title: type complexe
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: fac25ace69938e1245200e10285f4460ac216780
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948727"
---
# <a name="complex-type"></a><span data-ttu-id="e5a77-102">type complexe</span><span class="sxs-lookup"><span data-stu-id="e5a77-102">complex type</span></span>
<span data-ttu-id="e5a77-103">Un *type complexe* est un modèle permettant de définir des propriétés riches et structurées sur des [types d’entités](../../../../docs/framework/data/adonet/entity-type.md) ou sur d’autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="e5a77-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="e5a77-104">Chaque modèle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5a77-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="e5a77-105">Nom unique.</span><span class="sxs-lookup"><span data-stu-id="e5a77-105">A unique name.</span></span> <span data-ttu-id="e5a77-106">(Requis)</span><span class="sxs-lookup"><span data-stu-id="e5a77-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e5a77-107">Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e5a77-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="e5a77-108">Données sous la forme d’une ou de plusieurs [Propriétés](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="e5a77-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="e5a77-109">(Facultatif)</span><span class="sxs-lookup"><span data-stu-id="e5a77-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e5a77-110">Une propriété d'un type complexe peut être un autre type complexe.</span><span class="sxs-lookup"><span data-stu-id="e5a77-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="e5a77-111">Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="e5a77-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="e5a77-112">Toutefois, il existe des différences clés entre les types complexes et les types d'entités :</span><span class="sxs-lookup"><span data-stu-id="e5a77-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="e5a77-113">Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment.</span><span class="sxs-lookup"><span data-stu-id="e5a77-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="e5a77-114">Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="e5a77-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="e5a77-115">Les types complexes ne peuvent pas participer aux [associations](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="e5a77-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="e5a77-116">Aucune des terminaisons d’une association ne peut être un type complexe; par conséquent, les [Propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ne peuvent pas être définies sur des types complexes.</span><span class="sxs-lookup"><span data-stu-id="e5a77-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a77-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5a77-117">Example</span></span>  
 <span data-ttu-id="e5a77-118">Le [Entity Framework ADO.net](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="e5a77-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e5a77-119">Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="e5a77-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="e5a77-120">Pour définir le type complexe `Address` (ci-dessus) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité.</span><span class="sxs-lookup"><span data-stu-id="e5a77-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="e5a77-121">Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité (Publisher) :</span><span class="sxs-lookup"><span data-stu-id="e5a77-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a77-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5a77-122">See also</span></span>

- [<span data-ttu-id="e5a77-123">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="e5a77-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="e5a77-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="e5a77-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
