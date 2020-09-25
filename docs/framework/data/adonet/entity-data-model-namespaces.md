---
title: 'Entity Data Model : Espaces de noms'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 1e5f9527ec208c5650c68fe35bb758e0850b7700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194828"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="8943f-102">Entity Data Model : Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8943f-102">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="8943f-103">Un espace de noms dans le modèle EDM (Entity Data Model) est un conteneur abstrait pour les [types d’entité](entity-type.md), les [types complexes](complex-type.md)et les [associations](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="8943f-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="8943f-104">Les espaces de noms dans le modèle EDM sont semblables aux espaces de noms dans un langage de programmation : ils fournissent le contexte pour les objets qu'ils contiennent et offrent un moyen de lever l'ambiguïté entre les objets qui portent le même nom (mais qui sont contenus dans des espaces de noms différents).</span><span class="sxs-lookup"><span data-stu-id="8943f-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8943f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8943f-105">Example</span></span>  

 <span data-ttu-id="8943f-106">Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="8943f-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="8943f-107">Le CSDL suivant utilise un espace de noms pour identifier un type défini dans un modèle conceptuel différent.</span><span class="sxs-lookup"><span data-stu-id="8943f-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="8943f-108">L'exemple définit un type d'entité (`Publisher`) qui a une propriété de type complexe (`Address`) importée à partir de l'espace de noms `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="8943f-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="8943f-109">Notez que l'élément `Using` indique qu'un espace de noms a été importé.</span><span class="sxs-lookup"><span data-stu-id="8943f-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="8943f-110">Notez également que le type de la propriété `Address` est défini à l'aide de son nom qualifié complet (`ExtendedBooksModel.Address`), ce qui indique que ce type est défini dans l'espace de noms `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="8943f-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="8943f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8943f-111">See also</span></span>

- [<span data-ttu-id="8943f-112">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="8943f-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8943f-113">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="8943f-113">Entity Data Model</span></span>](entity-data-model.md)
