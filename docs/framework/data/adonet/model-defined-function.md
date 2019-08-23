---
title: fonction définie par modèle
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934518"
---
# <a name="model-defined-function"></a><span data-ttu-id="fc389-102">fonction définie par modèle</span><span class="sxs-lookup"><span data-stu-id="fc389-102">model-defined function</span></span>
<span data-ttu-id="fc389-103">Une *fonction définie par modèle* est une fonction définie dans un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="fc389-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="fc389-104">Le corps d’une fonction définie par modèle est exprimé en [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), ce qui permet d’exprimer la fonction indépendamment des règles ou des langages pris en charge dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="fc389-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="fc389-105">Une définition pour une fonction définie par modèle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc389-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="fc389-106">Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fc389-106">A function name.</span></span> <span data-ttu-id="fc389-107">(Requis)</span><span class="sxs-lookup"><span data-stu-id="fc389-107">(Required)</span></span>  
  
- <span data-ttu-id="fc389-108">Type de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="fc389-108">The type of the return value.</span></span> <span data-ttu-id="fc389-109">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="fc389-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fc389-110">Si aucun type de retour n’est spécifié, la valeur de retour est void.</span><span class="sxs-lookup"><span data-stu-id="fc389-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="fc389-111">Informations sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="fc389-111">Parameter information.</span></span> <span data-ttu-id="fc389-112">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="fc389-112">(Optional)</span></span>  
  
- <span data-ttu-id="fc389-113">Expression [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) qui définit le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fc389-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="fc389-114">Notez que les fonctions définies par modèle ne prennent pas en charge les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="fc389-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="fc389-115">Cette restriction est en place de manière à ce que des fonctions définies par modèle puissent être composées.</span><span class="sxs-lookup"><span data-stu-id="fc389-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc389-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="fc389-116">Example</span></span>  
 <span data-ttu-id="fc389-117">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="fc389-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Capture d’écran montrant un modèle avec la date de publication.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="fc389-119">Le [Entity Framework ADO.net](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="fc389-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="fc389-120">Le CSDL suivant définit une fonction dans le modèle conceptuel qui retourne le nombre d'années écoulées depuis la publication d'une instance de `Book` (dans le diagramme ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="fc389-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="fc389-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc389-121">See also</span></span>

- [<span data-ttu-id="fc389-122">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="fc389-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="fc389-123">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="fc389-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="fc389-124">Entity Data Model: Types de données primitifs</span><span class="sxs-lookup"><span data-stu-id="fc389-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
