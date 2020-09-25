---
title: type complexe
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203785"
---
# <a name="complex-type"></a><span data-ttu-id="2d10b-102">type complexe</span><span class="sxs-lookup"><span data-stu-id="2d10b-102">complex type</span></span>

<span data-ttu-id="2d10b-103">Un *type complexe* est un modèle permettant de définir des propriétés riches et structurées sur des [types d’entités](entity-type.md) ou sur d’autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="2d10b-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="2d10b-104">Chaque modèle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2d10b-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="2d10b-105">Nom unique.</span><span class="sxs-lookup"><span data-stu-id="2d10b-105">A unique name.</span></span> <span data-ttu-id="2d10b-106">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="2d10b-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d10b-107">Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2d10b-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="2d10b-108">Données sous la forme d’une ou de plusieurs [Propriétés](property.md).</span><span class="sxs-lookup"><span data-stu-id="2d10b-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="2d10b-109">(Facultatif.)</span><span class="sxs-lookup"><span data-stu-id="2d10b-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d10b-110">Une propriété d'un type complexe peut être un autre type complexe.</span><span class="sxs-lookup"><span data-stu-id="2d10b-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="2d10b-111">Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="2d10b-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="2d10b-112">Toutefois, il existe des différences clés entre les types complexes et les types d'entités :</span><span class="sxs-lookup"><span data-stu-id="2d10b-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="2d10b-113">Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment.</span><span class="sxs-lookup"><span data-stu-id="2d10b-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="2d10b-114">Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="2d10b-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="2d10b-115">Les types complexes ne peuvent pas participer aux [associations](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="2d10b-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="2d10b-116">Aucune des terminaisons d’une association ne peut être un type complexe ; par conséquent, les [Propriétés de navigation](navigation-property.md) ne peuvent pas être définies sur des types complexes.</span><span class="sxs-lookup"><span data-stu-id="2d10b-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d10b-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d10b-117">Example</span></span>  

 <span data-ttu-id="2d10b-118">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="2d10b-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="2d10b-119">Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="2d10b-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="2d10b-120">Pour définir le type complexe `Address` (ci-dessus) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité.</span><span class="sxs-lookup"><span data-stu-id="2d10b-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="2d10b-121">Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité (Publisher) :</span><span class="sxs-lookup"><span data-stu-id="2d10b-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="2d10b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d10b-122">See also</span></span>

- [<span data-ttu-id="2d10b-123">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="2d10b-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2d10b-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="2d10b-124">Entity Data Model</span></span>](entity-data-model.md)
