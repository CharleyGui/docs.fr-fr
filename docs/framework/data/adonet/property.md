---
title: propriété
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 6aeb29c5aa608987466ec858416a4ac141ff1da3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180918"
---
# <a name="property"></a><span data-ttu-id="79414-102">propriété</span><span class="sxs-lookup"><span data-stu-id="79414-102">property</span></span>

<span data-ttu-id="79414-103">Les *Propriétés* sont les blocs de construction fondamentaux des [types d’entité](entity-type.md) et des [types complexes](complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="79414-103">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="79414-104">Les propriétés définissent la forme et les caractéristiques des données qui sont contenues dans une instance de type d'entité ou une instance de type complexe.</span><span class="sxs-lookup"><span data-stu-id="79414-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="79414-105">Les propriétés dans un modèle conceptuel sont analogues aux propriétés définies sur une classe.</span><span class="sxs-lookup"><span data-stu-id="79414-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="79414-106">De même que les propriétés sur une classe définissent la forme de la classe et acheminent des informations sur les objets, les propriétés dans un modèle conceptuel définissent la forme d'un type d'entité et acheminent des informations sur les instances de type d'entité.</span><span class="sxs-lookup"><span data-stu-id="79414-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79414-107">Les propriétés, comme décrit dans cette rubrique, sont différentes des propriétés de navigation.</span><span class="sxs-lookup"><span data-stu-id="79414-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="79414-108">Pour plus d’informations, consultez [Propriétés de navigation](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="79414-108">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="79414-109">Une définition de propriété contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="79414-109">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="79414-110">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="79414-110">A property name.</span></span> <span data-ttu-id="79414-111">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="79414-111">(Required)</span></span>  
  
- <span data-ttu-id="79414-112">Type de propriété.</span><span class="sxs-lookup"><span data-stu-id="79414-112">A property type.</span></span> <span data-ttu-id="79414-113">(Obligatoire)</span><span class="sxs-lookup"><span data-stu-id="79414-113">(Required)</span></span>  
  
- <span data-ttu-id="79414-114">Ensemble de [facettes](facet.md).</span><span class="sxs-lookup"><span data-stu-id="79414-114">A set of [facets](facet.md).</span></span> <span data-ttu-id="79414-115">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="79414-115">(Optional)</span></span>  
  
 <span data-ttu-id="79414-116">Une propriété peut contenir des données de type primitif (comme une chaîne, un entier ou une valeur booléenne) ou des données structurées (comme un type complexe).</span><span class="sxs-lookup"><span data-stu-id="79414-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="79414-117">Les propriétés de type primitif sont également appelées des propriétés scalaires.</span><span class="sxs-lookup"><span data-stu-id="79414-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="79414-118">Pour plus d’informations, consultez [Entity Data Model : types de données primitifs](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="79414-118">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79414-119">Un type complexe peut lui-même avoir des propriétés qui sont des types complexes.</span><span class="sxs-lookup"><span data-stu-id="79414-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79414-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="79414-120">Example</span></span>  

 <span data-ttu-id="79414-121">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="79414-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="79414-122">Chaque type d'entité possède plusieurs propriétés, bien que les informations de type pour chaque propriété ne soient pas représentées dans le diagramme.</span><span class="sxs-lookup"><span data-stu-id="79414-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="79414-123">Les propriétés qui sont des [clés d’entité](entity-key.md) sont signalées par (Key).</span><span class="sxs-lookup"><span data-stu-id="79414-123">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="79414-125">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="79414-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="79414-126">Le CSDL suivant définit le type d'entité `Book` (tel que présenté dans le diagramme ci-dessus) et indique le type et le nom de chaque propriété à l'aide d'attributs XML.</span><span class="sxs-lookup"><span data-stu-id="79414-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="79414-127">Une facette facultative, `Nullable`, est également définie à l'aide d'un attribut XML.</span><span class="sxs-lookup"><span data-stu-id="79414-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="79414-128">Il est possible que l'une des propriétés présentées dans le diagramme soit une propriété de type complexe.</span><span class="sxs-lookup"><span data-stu-id="79414-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="79414-129">Par exemple, la propriété `Address` sur le type d'entité `Publisher` peut être une propriété de type complexe composée de plusieurs propriétés scalaires, telles que `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="79414-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="79414-130">Voici la représentation CSDL d'un tel type complexe :</span><span class="sxs-lookup"><span data-stu-id="79414-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="79414-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79414-131">See also</span></span>

- [<span data-ttu-id="79414-132">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="79414-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="79414-133">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="79414-133">Entity Data Model</span></span>](entity-data-model.md)
