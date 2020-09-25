---
title: conteneur d'entités
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95fb59c86f951e75f0988f45219fd07cbb003c01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200821"
---
# <a name="entity-container"></a><span data-ttu-id="24fff-102">conteneur d'entités</span><span class="sxs-lookup"><span data-stu-id="24fff-102">entity container</span></span>

<span data-ttu-id="24fff-103">Un *conteneur d’entités* est un regroupement logique de [jeux d’entités](entity-set.md), d' [ensembles d’associations](association-set.md)et d’importations de [fonctions](model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="24fff-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="24fff-104">Un conteneur d'entités défini dans un modèle conceptuel doit répondre aux spécifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="24fff-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="24fff-105">Au moins un conteneur d'entités doit être défini dans chaque modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="24fff-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="24fff-106">Le conteneur d'entités doit avoir un nom unique dans chaque modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="24fff-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="24fff-107">Un conteneur d'entités peut définir des jeux d'entités ou des ensembles d'associations qui utilisent des types d'entité ou des associations définis dans un ou plusieurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="24fff-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="24fff-108">Pour plus d’informations, consultez [Entity Data Model : Namespaces](entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="24fff-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fff-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="24fff-109">Example</span></span>  

 <span data-ttu-id="24fff-110">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="24fff-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="24fff-111">Pour plus d'informations, consultez l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="24fff-111">See the next example for more information.</span></span>  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="24fff-113">Bien que le diagramme n'achemine pas d'informations sur le conteneur d'entités, le modèle conceptuel doit définir un conteneur d'entités.</span><span class="sxs-lookup"><span data-stu-id="24fff-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="24fff-114">Le [Entity Framework ADO.net](./ef/index.md) utilise une DSL appelée Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="24fff-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="24fff-115">Le CSDL suivant définit un conteneur d'entités pour le modèle conceptuel présenté dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="24fff-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="24fff-116">Notez que le nom du conteneur d'entités est défini dans un attribut XML.</span><span class="sxs-lookup"><span data-stu-id="24fff-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="24fff-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24fff-117">See also</span></span>

- [<span data-ttu-id="24fff-118">Concepts clés d'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="24fff-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="24fff-119">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="24fff-119">Entity Data Model</span></span>](entity-data-model.md)
