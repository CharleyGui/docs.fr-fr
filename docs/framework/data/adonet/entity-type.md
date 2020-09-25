---
title: type d'entité
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3f99667a06d8aa439232802d4909290dfe9db97c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194776"
---
# <a name="entity-type"></a><span data-ttu-id="db5ba-102">type d'entité</span><span class="sxs-lookup"><span data-stu-id="db5ba-102">entity type</span></span>

<span data-ttu-id="db5ba-103">Le *type d’entité* est le bloc de construction fondamental pour la description de la structure des données avec le Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="db5ba-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="db5ba-104">Dans un modèle conceptuel, un type d'entité représente la structure des concepts de niveau supérieur, comme les clients ou les commandes.</span><span class="sxs-lookup"><span data-stu-id="db5ba-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="db5ba-105">Un type d'entité est un modèle pour les instances de type d'entité.</span><span class="sxs-lookup"><span data-stu-id="db5ba-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="db5ba-106">Chaque modèle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="db5ba-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="db5ba-107">Nom unique.</span><span class="sxs-lookup"><span data-stu-id="db5ba-107">A unique name.</span></span> <span data-ttu-id="db5ba-108">(Obligatoire.)</span><span class="sxs-lookup"><span data-stu-id="db5ba-108">(Required.)</span></span>  
  
- <span data-ttu-id="db5ba-109">[Clé d’entité](entity-key.md) définie par une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="db5ba-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="db5ba-110">(Obligatoire.)</span><span class="sxs-lookup"><span data-stu-id="db5ba-110">(Required.)</span></span>  
  
- <span data-ttu-id="db5ba-111">Données sous la forme de [Propriétés](property.md).</span><span class="sxs-lookup"><span data-stu-id="db5ba-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="db5ba-112">(Facultatif.)</span><span class="sxs-lookup"><span data-stu-id="db5ba-112">(Optional.)</span></span>  
  
- <span data-ttu-id="db5ba-113">[Propriétés de navigation](navigation-property.md) qui permettent de naviguer d’une [terminaison](association-end.md) d’une [Association](association-type.md) à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="db5ba-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="db5ba-114">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="db5ba-114">(Optional)</span></span>  
  
 <span data-ttu-id="db5ba-115">Dans une application, une instance d'un type d'entité représente un objet spécifique (tel qu'un client ou une commande spécifique).</span><span class="sxs-lookup"><span data-stu-id="db5ba-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="db5ba-116">Chaque instance d’un type d’entité doit avoir une [clé d’entité](entity-key.md) unique dans un [jeu d’entités](entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="db5ba-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="db5ba-117">Deux instances de type d'entité sont considérées égales seulement si elles sont du même type et si les valeurs de leurs clés d'entité sont identiques.</span><span class="sxs-lookup"><span data-stu-id="db5ba-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db5ba-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="db5ba-118">Example</span></span>  

 <span data-ttu-id="db5ba-119">Le diagramme suivant montre un modèle conceptuel avec trois types d'entité : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="db5ba-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="db5ba-121">Notez que les propriétés de chaque type d'entité qui composent sa clé d'entité sont signalées par « (Key) ».</span><span class="sxs-lookup"><span data-stu-id="db5ba-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="db5ba-122">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="db5ba-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="db5ba-123">Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="db5ba-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="db5ba-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db5ba-124">See also</span></span>

- [<span data-ttu-id="db5ba-125">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="db5ba-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="db5ba-126">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="db5ba-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="db5ba-127">articulaire</span><span class="sxs-lookup"><span data-stu-id="db5ba-127">facet</span></span>](facet.md)
