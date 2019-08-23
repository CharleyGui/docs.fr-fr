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
ms.openlocfilehash: 5b135fee12ac5b78b41a657f2eb458ea104143fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923932"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="cdba9-102">Indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="cdba9-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="cdba9-103">Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux.</span><span class="sxs-lookup"><span data-stu-id="cdba9-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="cdba9-104">La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="cdba9-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="cdba9-105">Les indexeurs s’apparentent aux [propriétés](../classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="cdba9-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="cdba9-106">L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="cdba9-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="cdba9-107">La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="cdba9-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="cdba9-108">Pour plus d’exemples, consultez [Rubriques connexes](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="cdba9-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="cdba9-109">Définitions de corps d'expression</span><span class="sxs-lookup"><span data-stu-id="cdba9-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="cdba9-110">Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur.</span><span class="sxs-lookup"><span data-stu-id="cdba9-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="cdba9-111">Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="cdba9-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="cdba9-112">À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cdba9-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="cdba9-113">Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="cdba9-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="cdba9-114">À partir de C# 7.0, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="cdba9-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="cdba9-115">Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="cdba9-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="cdba9-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cdba9-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="cdba9-117">Vue d'ensemble des indexeurs</span><span class="sxs-lookup"><span data-stu-id="cdba9-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="cdba9-118">Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="cdba9-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="cdba9-119">Un accesseur `get` retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="cdba9-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="cdba9-120">Un accesseur `set` affecte une valeur.</span><span class="sxs-lookup"><span data-stu-id="cdba9-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="cdba9-121">Le mot clé [this](../../language-reference/keywords/this.md) est utilisé pour définir l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="cdba9-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="cdba9-122">Le mot clé [value](../../language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.</span><span class="sxs-lookup"><span data-stu-id="cdba9-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="cdba9-123">Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.</span><span class="sxs-lookup"><span data-stu-id="cdba9-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="cdba9-124">Les indexeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="cdba9-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="cdba9-125">Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="cdba9-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="cdba9-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="cdba9-126">Related Sections</span></span>  
  
- [<span data-ttu-id="cdba9-127">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="cdba9-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="cdba9-128">Indexeurs dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="cdba9-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="cdba9-129">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="cdba9-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="cdba9-130">Restriction d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="cdba9-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="cdba9-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cdba9-131">C# Language Specification</span></span>  

<span data-ttu-id="cdba9-132">Pour plus d’informations, consultez [Indexeurs](~/_csharplang/spec/classes.md#indexers) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="cdba9-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="cdba9-133">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="cdba9-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cdba9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdba9-134">See also</span></span>

- [<span data-ttu-id="cdba9-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cdba9-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cdba9-136">Propriétés</span><span class="sxs-lookup"><span data-stu-id="cdba9-136">Properties</span></span>](../classes-and-structs/properties.md)
