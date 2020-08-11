---
title: System.Delegate et le mot clé `delegate`
description: Découvrez les classes dans .NET qui prennent en charge les délégués et comment ces derniers sont mappés au mot clé’Delegate'.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062461"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="d0889-103">System.Delegate et le mot clé `delegate`</span><span class="sxs-lookup"><span data-stu-id="d0889-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="d0889-104">Précédent</span><span class="sxs-lookup"><span data-stu-id="d0889-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="d0889-105">Cet article décrit les classes dans .NET qui prennent en charge les délégués et comment elles sont mappées au `delegate` mot clé.</span><span class="sxs-lookup"><span data-stu-id="d0889-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="d0889-106">Définir les types délégués</span><span class="sxs-lookup"><span data-stu-id="d0889-106">Define delegate types</span></span>

<span data-ttu-id="d0889-107">Commençons par le mot clé 'delegate', car c’est l’élément principal que vous utilisez quand vous travaillez avec des délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="d0889-108">Le code que le compilateur génère quand vous utilisez le mot clé `delegate` mappe aux appels de méthode qui appellent des membres des classes <xref:System.Delegate> et <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="d0889-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="d0889-109">Vous définissez un type délégué à l’aide d’une syntaxe similaire à la définition d’une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="d0889-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="d0889-110">Vous venez d’ajouter le mot clé `delegate` à la définition.</span><span class="sxs-lookup"><span data-stu-id="d0889-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="d0889-111">Continuons à utiliser la méthode List.Sort() comme dans notre exemple.</span><span class="sxs-lookup"><span data-stu-id="d0889-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="d0889-112">La première étape consiste à créer un type pour le délégué de comparaison :</span><span class="sxs-lookup"><span data-stu-id="d0889-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="d0889-113">Le compilateur génère une classe, dérivée de `System.Delegate`, qui correspond à la signature utilisée (dans le cas présent, une méthode qui retourne un entier et qui a deux arguments).</span><span class="sxs-lookup"><span data-stu-id="d0889-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="d0889-114">Le type de ce délégué est `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="d0889-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="d0889-115">Le type délégué `Comparison` est un type générique.</span><span class="sxs-lookup"><span data-stu-id="d0889-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="d0889-116">Pour plus d’informations sur les génériques, cliquez [ici](programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0889-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="d0889-117">Notez que la syntaxe peut sembler déclarer une variable, alors qu’elle déclare en fait un *type*.</span><span class="sxs-lookup"><span data-stu-id="d0889-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="d0889-118">Vous pouvez définir des types délégués dans des classes, directement dans des espaces de noms, ou même dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="d0889-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="d0889-119">La déclaration de types délégués (ou d’autres types) directement dans l’espace de noms global n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="d0889-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="d0889-120">Le compilateur génère également des gestionnaires d’ajout et de suppression pour ce nouveau type, afin que les clients de cette classe puissent ajouter et supprimer des méthodes dans la liste d’invocation d’une instance.</span><span class="sxs-lookup"><span data-stu-id="d0889-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="d0889-121">Le compilateur exige que la signature de la méthode ajoutée ou supprimée corresponde à la signature utilisée lors de la déclaration de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d0889-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="d0889-122">Déclarer des instances de délégués</span><span class="sxs-lookup"><span data-stu-id="d0889-122">Declare instances of delegates</span></span>

<span data-ttu-id="d0889-123">Après avoir défini le délégué, vous pouvez créer une instance de ce type.</span><span class="sxs-lookup"><span data-stu-id="d0889-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="d0889-124">Comme pour toutes les variables en C#, vous ne pouvez pas déclarer d’instances de délégué directement dans un espace de noms, ni dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="d0889-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="d0889-125">Le type de la variable est le type délégué défini précédemment, `Comparison<T>`.</span><span class="sxs-lookup"><span data-stu-id="d0889-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="d0889-126">Le nom de la variable est `comparator`.</span><span class="sxs-lookup"><span data-stu-id="d0889-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="d0889-127">Cet extrait de code ci-dessus a déclaré une variable membre à l’intérieur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="d0889-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="d0889-128">Vous pouvez également déclarer des variables de délégués qui sont des variables locales, ou bien des arguments de méthodes.</span><span class="sxs-lookup"><span data-stu-id="d0889-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="d0889-129">Appeler des délégués</span><span class="sxs-lookup"><span data-stu-id="d0889-129">Invoke delegates</span></span>

<span data-ttu-id="d0889-130">Vous appelez les méthodes qui se trouvent dans la liste d’invocation d’un délégué en appelant ce dernier.</span><span class="sxs-lookup"><span data-stu-id="d0889-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="d0889-131">À l’intérieur de la méthode `Sort()`, le code appelle la méthode de comparaison pour déterminer l’ordre dans lequel placer les objets :</span><span class="sxs-lookup"><span data-stu-id="d0889-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="d0889-132">Dans la ligne ci-dessus, le code *appelle* la méthode attachée au délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="d0889-133">Vous traitez la variable comme un nom de méthode et vous l’appelez à l’aide de la syntaxe d’appel de méthode normale.</span><span class="sxs-lookup"><span data-stu-id="d0889-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="d0889-134">Cette ligne de code effectue une hypothèse hasardeuse : il n’existe aucune garantie qu’une cible a été ajoutée au délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="d0889-135">Si aucune cible n’a été attachée, la ligne ci-dessus entraîne la levée de `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="d0889-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="d0889-136">Les idiomes utilisés pour résoudre ce problème sont plus compliqués qu’un simple contrôle de valeur Null. Ils sont traités plus loin dans cette [série](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="d0889-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="d0889-137">Assigner, ajouter et supprimer des cibles d’appel</span><span class="sxs-lookup"><span data-stu-id="d0889-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="d0889-138">Voyons comment un type délégué est défini et comment les instances de délégué sont déclarées et appelées.</span><span class="sxs-lookup"><span data-stu-id="d0889-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="d0889-139">Les développeurs qui souhaitent utiliser la méthode `List.Sort()` doivent définir une méthode dont la signature correspond à la définition du type délégué, puis l’assigner au délégué utilisé par la méthode sort.</span><span class="sxs-lookup"><span data-stu-id="d0889-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="d0889-140">Cette assignation ajoute la méthode à la liste d’invocation de cet objet délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="d0889-141">Supposons que vous souhaitiez trier une liste de chaînes en fonction de leur longueur.</span><span class="sxs-lookup"><span data-stu-id="d0889-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="d0889-142">Votre fonction de comparaison peut être la suivante :</span><span class="sxs-lookup"><span data-stu-id="d0889-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="d0889-143">La méthode est déclarée en tant que méthode privée.</span><span class="sxs-lookup"><span data-stu-id="d0889-143">The method is declared as a private method.</span></span> <span data-ttu-id="d0889-144">C’est parfait.</span><span class="sxs-lookup"><span data-stu-id="d0889-144">That's fine.</span></span> <span data-ttu-id="d0889-145">Vous ne voulez peut-être pas que cette méthode fasse partie de votre interface publique.</span><span class="sxs-lookup"><span data-stu-id="d0889-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="d0889-146">Elle peut toujours être utilisée comme méthode de comparaison quand elle est attachée à un délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="d0889-147">Cette méthode est attachée à la liste cible de l’objet délégué dans le code appelant, qui peut y accéder par l’intermédiaire de ce délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="d0889-148">Vous créez cette relation en passant cette méthode à la méthode `List.Sort()` :</span><span class="sxs-lookup"><span data-stu-id="d0889-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="d0889-149">Notez que le nom de la méthode est utilisé sans parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d0889-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="d0889-150">L’utilisation de la méthode comme argument indique au compilateur de convertir la référence de méthode en une référence pouvant être utilisée comme cible d’invocation de délégué, puis d’attacher cette méthode comme cible d’invocation.</span><span class="sxs-lookup"><span data-stu-id="d0889-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="d0889-151">Vous pouvez également avoir déclaré explicitement une variable de type `Comparison<string>` et effectué une assignation :</span><span class="sxs-lookup"><span data-stu-id="d0889-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="d0889-152">Quand la méthode utilisée comme cible du délégué est petite, il est courant d’utiliser la syntaxe des [expressions lambda](language-reference/operators/lambda-expressions.md) pour effectuer l’assignation :</span><span class="sxs-lookup"><span data-stu-id="d0889-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](language-reference/operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="d0889-153">L’utilisation d’expressions lambda pour les cibles de délégué est traitée plus loin dans une [section ultérieure](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="d0889-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="d0889-154">L’exemple Sort() attache généralement une méthode cible unique au délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="d0889-155">Toutefois, les objets délégués prennent en charge les listes d’invocation comprenant plusieurs méthodes cibles attachées à un objet délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="d0889-156">Classes Delegate et MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="d0889-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="d0889-157">La prise en charge du langage décrite ci-dessus fournit les fonctionnalités et la prise en charge généralement nécessaires pour utiliser des délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="d0889-158">Ces fonctionnalités sont basées sur deux classes du framework .NET Core : <xref:System.Delegate> et <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="d0889-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="d0889-159">La `System.Delegate` classe et sa sous-classe directe unique, `System.MulticastDelegate` fournissent la prise en charge de l’infrastructure pour la création de délégués, l’inscription de méthodes en tant que cibles de délégué et l’appel de toutes les méthodes inscrites en tant que cible de délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="d0889-160">Il est intéressant de noter que les classes `System.Delegate` et `System.MulticastDelegate` ne sont pas elles-mêmes des types délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="d0889-161">Elles servent de base à tous les types délégués spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d0889-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="d0889-162">Ce même processus de conception du langage a stipulé que vous ne pouvez pas déclarer une classe qui dérive de `Delegate` ou de `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="d0889-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="d0889-163">Les règles du langage C# l’interdisent.</span><span class="sxs-lookup"><span data-stu-id="d0889-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="d0889-164">À la place, le compilateur C# crée des instances d’une classe dérivée de `MulticastDelegate` quand vous utilisez le mot clé du langage C# pour déclarer des types délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="d0889-165">Cette conception trouve ses racines dans la première version Release de C# et du .NET.</span><span class="sxs-lookup"><span data-stu-id="d0889-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="d0889-166">L’équipe de conception avait pour objectif de s’assurer que le langage appliquait la cohérence des types lors de l’utilisation de délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="d0889-167">Il était important de garantir que les délégués étaient appelés avec le type et le nombre d’arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="d0889-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="d0889-168">Et que tout type de retour était correctement indiqué au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d0889-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="d0889-169">Les délégués faisaient partie de la version Release du .NET 1.0, qui était antérieure aux génériques.</span><span class="sxs-lookup"><span data-stu-id="d0889-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="d0889-170">La création, par le compilateur, des classes déléguées concrètes qui représentaient la signature de méthode utilisée constituait la meilleure façon d’appliquer la cohérence des types.</span><span class="sxs-lookup"><span data-stu-id="d0889-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="d0889-171">Même si vous ne pouvez pas créer des classes dérivées directement, vous utiliserez les méthodes définies sur ces classes.</span><span class="sxs-lookup"><span data-stu-id="d0889-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="d0889-172">Examinons les méthodes les plus courantes que vous utiliserez quand vous travaillerez avec des délégués.</span><span class="sxs-lookup"><span data-stu-id="d0889-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="d0889-173">Le premier et le plus important point à retenir est que chaque délégué avec lequel vous travaillez est dérivé de `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="d0889-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="d0889-174">Un délégué multicast signifie que plusieurs méthodes cibles peuvent être appelées lors d’un appel par l’intermédiaire d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="d0889-175">La conception d’origine envisageait de distinguer les délégués où une seule méthode cible pouvait être attachée et appelée, et les délégués où plusieurs méthodes cibles pouvaient être attachées et appelées.</span><span class="sxs-lookup"><span data-stu-id="d0889-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="d0889-176">En réalité, cette distinction s’est avérée moins utile que prévu.</span><span class="sxs-lookup"><span data-stu-id="d0889-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="d0889-177">Les deux différentes classes étaient déjà créées et sont présentes dans le framework depuis la première version Release publique de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d0889-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="d0889-178">Les méthodes que vous utiliserez le plus avec les délégués sont `Invoke()` et `BeginInvoke()` / `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="d0889-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="d0889-179">`Invoke()` appelle toutes les méthodes qui ont été attachées à une instance de délégué particulière.</span><span class="sxs-lookup"><span data-stu-id="d0889-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="d0889-180">Comme vous l’avez vu ci-dessus, vous appelez généralement des délégués à l’aide de la syntaxe d’appel de méthode sur la variable de délégué.</span><span class="sxs-lookup"><span data-stu-id="d0889-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="d0889-181">Comme vous le verrez [plus loin dans cette série](delegates-patterns.md), il existe des modèles qui fonctionnent directement avec ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="d0889-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="d0889-182">Maintenant que vous avez vu la syntaxe du langage et les classes qui prennent en charge les délégués, examinons la façon dont les délégués fortement typés sont utilisés, créés et appelés.</span><span class="sxs-lookup"><span data-stu-id="d0889-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="d0889-183">Next</span><span class="sxs-lookup"><span data-stu-id="d0889-183">Next</span></span>](delegates-strongly-typed.md)
