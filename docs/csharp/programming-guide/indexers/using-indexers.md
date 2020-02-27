---
title: Utiliser des indexeurs - Guide de programmation C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628161"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="99e72-102">Utiliser des indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="99e72-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="99e72-103">Les indexeurs simplifient, d’un point de vue syntaxique, la création d’une [classe](../../language-reference/keywords/class.md), d’un [struct](../../language-reference/builtin-types/struct.md) ou d’une [interface](../../language-reference/keywords/interface.md) auxquels les applications clientes peuvent accéder exactement comme à un tableau.</span><span class="sxs-lookup"><span data-stu-id="99e72-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="99e72-104">Le plus souvent, les indexeurs sont implémentés dans les types dont l’objectif premier est d’encapsuler une collection ou un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="99e72-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="99e72-105">Prenons l’exemple d’une classe `TempRecord` qui représente la température, en Fahrenheit, enregistrée à 10 moments différents sur une période de 24 heures.</span><span class="sxs-lookup"><span data-stu-id="99e72-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="99e72-106">Elle contient un tableau `temps` de type `float[]` pour stocker les valeurs de température.</span><span class="sxs-lookup"><span data-stu-id="99e72-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="99e72-107">En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance `TempRecord` sous la forme `float temp = tr[4]` et non sous la forme `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="99e72-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="99e72-108">La notation d’indexeur simplifie non seulement la syntaxe pour les applications clientes, mais elle permet également aux autres développeurs de comprendre de façon plus intuitive l’objectif de la classe.</span><span class="sxs-lookup"><span data-stu-id="99e72-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="99e72-109">Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../language-reference/keywords/this.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="99e72-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="99e72-110">Notes</span><span class="sxs-lookup"><span data-stu-id="99e72-110">Remarks</span></span>

<span data-ttu-id="99e72-111">Le type d’un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l’indexeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="99e72-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="99e72-112">Pour plus d’informations sur les niveaux d’accessibilité, consultez [Modificateurs d’accès](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="99e72-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="99e72-113">Pour plus d’informations sur l’utilisation d’indexeurs avec une interface, consultez [Indexeurs d’interface](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="99e72-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="99e72-114">La signature d’un indexeur est composée du nombre et des types de ses paramètres formels.</span><span class="sxs-lookup"><span data-stu-id="99e72-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="99e72-115">Elle ne comporte ni le type de l’indexeur ni le nom des paramètres formels.</span><span class="sxs-lookup"><span data-stu-id="99e72-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="99e72-116">Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="99e72-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="99e72-117">Une valeur d’indexeur n’est pas classée comme variable ; vous ne pouvez donc pas la passer comme paramètre [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="99e72-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="99e72-118">Pour affecter à l’indexeur un nom exploitable dans d’autres langages, utilisez <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="99e72-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="99e72-119">Cet indexeur portera le nom `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="99e72-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="99e72-120">Si vous ne précisez pas le nom de l’attribut, `Item` est utilisé comme nom par défaut.</span><span class="sxs-lookup"><span data-stu-id="99e72-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="99e72-121">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="99e72-121">Example 1</span></span>  
  
<span data-ttu-id="99e72-122">L’exemple suivant montre comment déclarer un champ de tableau privé `temps`, et un indexeur.</span><span class="sxs-lookup"><span data-stu-id="99e72-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="99e72-123">L’indexeur permet d’accéder directement à l’instance `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="99e72-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="99e72-124">Comme alternative à l’utilisation de l’indexeur, vous pouvez déclarer le tableau comme membre [public](../../language-reference/keywords/public.md) et accéder directement à ses membres, `tempRecord.temps[i]`.</span><span class="sxs-lookup"><span data-stu-id="99e72-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="99e72-125">Notez que quand l’accès à un indexeur est évalué, par exemple dans une instruction `Console.Write`, l’accesseur [get](../../language-reference/keywords/get.md) est appelé.</span><span class="sxs-lookup"><span data-stu-id="99e72-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="99e72-126">C’est pourquoi une erreur de compilation se produit s’il n’existe aucun accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="99e72-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="99e72-127">Indexation avec d’autres valeurs</span><span class="sxs-lookup"><span data-stu-id="99e72-127">Indexing using other values</span></span>

<span data-ttu-id="99e72-128">C# ne limite pas le type de paramètre d’indexeur au type entier.</span><span class="sxs-lookup"><span data-stu-id="99e72-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="99e72-129">Par exemple, il peut être utile d’utiliser une chaîne avec un indexeur.</span><span class="sxs-lookup"><span data-stu-id="99e72-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="99e72-130">Il est possible d’implémenter un tel indexeur en recherchant la chaîne dans la collection et en retournant la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="99e72-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="99e72-131">Comme les accesseurs peuvent être surchargés, les versions chaîne et entier peuvent coexister.</span><span class="sxs-lookup"><span data-stu-id="99e72-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="99e72-132">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="99e72-132">Example 2</span></span>  
  
<span data-ttu-id="99e72-133">L’exemple suivant déclare une classe qui stocke les jours de la semaine.</span><span class="sxs-lookup"><span data-stu-id="99e72-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="99e72-134">Un accesseur `get` prend une chaîne, le nom d’un jour, et retourne l’entier correspondant.</span><span class="sxs-lookup"><span data-stu-id="99e72-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="99e72-135">Par exemple, « Sunday » retourne 0, « Monday » retourne 1 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="99e72-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="99e72-136">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="99e72-136">Robust programming</span></span>

 <span data-ttu-id="99e72-137">La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :</span><span class="sxs-lookup"><span data-stu-id="99e72-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="99e72-138">N’oubliez pas d’incorporer une stratégie de gestion des erreurs au cas où le code client passerait une valeur d’index non valide.</span><span class="sxs-lookup"><span data-stu-id="99e72-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="99e72-139">Dans le premier exemple décrit plus haut dans cette rubrique, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l’entrée avant de la passer à l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="99e72-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="99e72-140">Vous pouvez également placer le code de gestion des erreurs à l’intérieur de l’indexeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="99e72-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="99e72-141">N’oubliez pas d’indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="99e72-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="99e72-142">Définissez pour les accesseurs [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) une accessibilité aussi restrictive que possible.</span><span class="sxs-lookup"><span data-stu-id="99e72-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="99e72-143">Cela est particulièrement important dans le cas de l’accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="99e72-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="99e72-144">Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="99e72-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e72-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99e72-145">See also</span></span>

- [<span data-ttu-id="99e72-146">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="99e72-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="99e72-147">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="99e72-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="99e72-148">Propriétés</span><span class="sxs-lookup"><span data-stu-id="99e72-148">Properties</span></span>](../classes-and-structs/properties.md)
