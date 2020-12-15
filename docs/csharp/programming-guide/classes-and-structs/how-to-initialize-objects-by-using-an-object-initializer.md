---
title: Comment initialiser des objets à l’aide d’un initialiseur d’objet-Guide de programmation C#
description: Découvrez comment utiliser des initialiseurs d’objets pour initialiser des objets de type en C# sans appeler un constructeur. Utilisez un initialiseur d’objet pour définir un type anonyme.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0c2d38713a1fdefd922234a02e23518c0f00add5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512780"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="498e9-104">Comment initialiser des objets à l’aide d’un initialiseur d’objet (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="498e9-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="498e9-105">Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets de type de façon déclarative sans appeler explicitement un constructeur pour le type.</span><span class="sxs-lookup"><span data-stu-id="498e9-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="498e9-106">Les exemples suivants montrent comment utiliser des initialiseurs d’objets avec des objets nommés.</span><span class="sxs-lookup"><span data-stu-id="498e9-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="498e9-107">Le compilateur traite les initialiseurs d’objets en accédant tout d’abord au constructeur d’instance sans paramètre, puis en traitant les initialisations de membres.</span><span class="sxs-lookup"><span data-stu-id="498e9-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="498e9-108">Ainsi, si le constructeur sans paramètre est déclaré comme `private` dans la classe, les initialiseurs d’objets qui nécessitent un accès public échoueront.</span><span class="sxs-lookup"><span data-stu-id="498e9-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="498e9-109">Vous devez utiliser un initialiseur d’objet si vous définissez un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="498e9-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="498e9-110">Pour plus d’informations, consultez [Comment retourner des sous-ensembles de propriétés d’éléments dans une requête](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="498e9-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="498e9-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="498e9-111">Example</span></span>  

<span data-ttu-id="498e9-112">L’exemple suivant montre comment initialiser un nouveau type `StudentName` à l’aide d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="498e9-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="498e9-113">Cet exemple définit des propriétés dans le type `StudentName` :</span><span class="sxs-lookup"><span data-stu-id="498e9-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="498e9-114">Des initialiseurs d’objet peuvent être utilisés pour définir des indexeurs dans un objet.</span><span class="sxs-lookup"><span data-stu-id="498e9-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="498e9-115">L’exemple suivant définit une classe `BaseballTeam` qui utilise un indexeur pour obtenir et définir des joueurs à des positions différentes.</span><span class="sxs-lookup"><span data-stu-id="498e9-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="498e9-116">L’initialiseur peut affecter des joueurs en fonction de l’abréviation de la position ou du chiffre utilisé pour désigner la position sur les feuilles de match :</span><span class="sxs-lookup"><span data-stu-id="498e9-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="498e9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="498e9-117">See also</span></span>

- [<span data-ttu-id="498e9-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="498e9-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="498e9-119">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="498e9-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
