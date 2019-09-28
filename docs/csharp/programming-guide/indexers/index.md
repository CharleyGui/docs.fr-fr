---
title: Indexeurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: f0df3170289d780852ee14232e92c3b71412c548
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392381"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="d55b4-102">Indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d55b4-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="d55b4-103">Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux.</span><span class="sxs-lookup"><span data-stu-id="d55b4-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="d55b4-104">La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="d55b4-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="d55b4-105">Les indexeurs s’apparentent aux [propriétés](../classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="d55b4-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="d55b4-106">L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="d55b4-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="d55b4-107">La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="d55b4-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="d55b4-108">Pour plus d’exemples, consultez [Rubriques connexes](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="d55b4-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="d55b4-109">Définitions de corps d'expression</span><span class="sxs-lookup"><span data-stu-id="d55b4-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="d55b4-110">Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur.</span><span class="sxs-lookup"><span data-stu-id="d55b4-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="d55b4-111">Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="d55b4-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="d55b4-112">À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d55b4-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="d55b4-113">Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d55b4-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="d55b4-114">À partir de C# 7.0, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="d55b4-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="d55b4-115">Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="d55b4-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="d55b4-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d55b4-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="d55b4-117">Vue d'ensemble des indexeurs</span><span class="sxs-lookup"><span data-stu-id="d55b4-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="d55b4-118">Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="d55b4-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="d55b4-119">Un accesseur `get` retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="d55b4-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="d55b4-120">Un accesseur `set` affecte une valeur.</span><span class="sxs-lookup"><span data-stu-id="d55b4-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="d55b4-121">Le mot clé [this](../../language-reference/keywords/this.md) est utilisé pour définir l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="d55b4-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="d55b4-122">Le mot clé [value](../../language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.</span><span class="sxs-lookup"><span data-stu-id="d55b4-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="d55b4-123">Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.</span><span class="sxs-lookup"><span data-stu-id="d55b4-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="d55b4-124">Les indexeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="d55b4-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="d55b4-125">Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="d55b4-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="d55b4-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d55b4-126">Related Sections</span></span>  
  
- [<span data-ttu-id="d55b4-127">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="d55b4-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="d55b4-128">Indexeurs dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="d55b4-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="d55b4-129">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="d55b4-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="d55b4-130">Restriction d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="d55b4-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d55b4-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d55b4-131">C# Language Specification</span></span>  

<span data-ttu-id="d55b4-132">Pour plus d’informations, consultez [Indexeurs](~/_csharplang/spec/classes.md#indexers) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d55b4-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="d55b4-133">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="d55b4-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d55b4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d55b4-134">See also</span></span>

- [<span data-ttu-id="d55b4-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d55b4-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d55b4-136">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d55b4-136">Properties</span></span>](../classes-and-structs/properties.md)
