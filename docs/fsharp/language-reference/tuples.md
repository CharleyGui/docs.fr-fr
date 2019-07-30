---
title: Tuples
description: En savoir plus F# sur le tuple, un regroupement de valeurs sans nom, mais ordonnées, peut-être de types différents.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630242"
---
# <a name="tuples"></a><span data-ttu-id="7ba4e-103">Tuples</span><span class="sxs-lookup"><span data-stu-id="7ba4e-103">Tuples</span></span>

<span data-ttu-id="7ba4e-104">Un *Tuple* est un regroupement de valeurs sans nom, mais ordonnées, peut-être de types différents.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="7ba4e-105">Les tuples peuvent être des types référence ou des structs.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ba4e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ba4e-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="7ba4e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7ba4e-107">Remarks</span></span>

<span data-ttu-id="7ba4e-108">Chaque *élément* de la syntaxe précédente peut être n’importe F# quelle expression valide.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="7ba4e-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="7ba4e-109">Examples</span></span>

<span data-ttu-id="7ba4e-110">Les exemples de tuples incluent des paires, des triples, etc., du même type ou de types différents.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="7ba4e-111">Quelques exemples sont illustrés dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="7ba4e-112">Obtention de valeurs individuelles</span><span class="sxs-lookup"><span data-stu-id="7ba4e-112">Obtaining Individual Values</span></span>

<span data-ttu-id="7ba4e-113">Vous pouvez utiliser des critères spéciaux pour accéder et assigner des noms pour les éléments de tuple, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="7ba4e-114">Vous pouvez également déconstruire un tuple via des critères spéciaux en dehors `match` d’une `let` expression via la liaison:</span><span class="sxs-lookup"><span data-stu-id="7ba4e-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="7ba4e-115">Vous pouvez aussi répéter les correspondances sur les tuples en tant qu’entrées dans les fonctions:</span><span class="sxs-lookup"><span data-stu-id="7ba4e-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="7ba4e-116">Si vous n’avez besoin que d’un seul élément du tuple, le caractère générique (le trait de soulignement) peut être utilisé pour éviter de créer un nouveau nom pour une valeur dont vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="7ba4e-117">La copie d’éléments d’un tuple de référence dans un tuple de struct est également simple:</span><span class="sxs-lookup"><span data-stu-id="7ba4e-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="7ba4e-118">Les fonctions `fst` et `snd` (tuples de référence uniquement) retournent respectivement le premier et le deuxième élément d’un tuple.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="7ba4e-119">Il n’existe aucune fonction intégrée qui retourne le troisième élément d’un triple, mais vous pouvez facilement en écrire un comme suit.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="7ba4e-120">En règle générale, il est préférable d’utiliser des critères spéciaux pour accéder à des éléments de tuple individuels.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="7ba4e-121">Utilisation de tuples</span><span class="sxs-lookup"><span data-stu-id="7ba4e-121">Using Tuples</span></span>

<span data-ttu-id="7ba4e-122">Les tuples offrent un moyen pratique de retourner plusieurs valeurs à partir d’une fonction, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="7ba4e-123">Cet exemple exécute une division d’entier et retourne le résultat arrondi de l’opération en tant que premier membre d’une paire de tuples et le reste comme deuxième membre de la paire.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="7ba4e-124">Les tuples peuvent également être utilisés en tant qu’arguments de fonction lorsque vous souhaitez éviter la curryfication implicite des arguments de fonction qui est impliquée par la syntaxe de fonction habituelle.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="7ba4e-125">La syntaxe habituelle pour définir la fonction `let sum a b = a + b` vous permet de définir une fonction qui est l’application partielle du premier argument de la fonction, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="7ba4e-126">L’utilisation d’un tuple comme paramètre désactive la curryfication.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="7ba4e-127">Pour plus d’informations, consultez «application partielle d’arguments» dans les [fonctions](./functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ba4e-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="7ba4e-128">Noms de types de tuples</span><span class="sxs-lookup"><span data-stu-id="7ba4e-128">Names of Tuple Types</span></span>

<span data-ttu-id="7ba4e-129">Lorsque vous écrivez le nom d’un type qui est un tuple, vous utilisez le `*` symbole pour séparer les éléments.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="7ba4e-130">Pour un tuple qui se compose d' `int`un, `float`d’un et `string`d’un, `(10, 10.0, "ten")`tel que, le type serait écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="7ba4e-131">Interopérabilité avec C# les tuples</span><span class="sxs-lookup"><span data-stu-id="7ba4e-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="7ba4e-132">C#7,0 a introduit des tuples dans le langage.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="7ba4e-133">Les tuples C# dans sont des structs et sont équivalents aux tuples F#de struct dans.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="7ba4e-134">Si vous devez interagir avec, vous C#devez utiliser des tuples de struct.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="7ba4e-135">C’est facile à faire.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-135">This is easy to do.</span></span>  <span data-ttu-id="7ba4e-136">Par exemple, imaginez que vous devez passer un tuple à une C# classe, puis utiliser son résultat, qui est également un tuple:</span><span class="sxs-lookup"><span data-stu-id="7ba4e-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="7ba4e-137">Dans votre F# code, vous pouvez ensuite passer un tuple de struct comme paramètre et utiliser le résultat comme un tuple de struct.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="7ba4e-138">Conversion entre les tuples de référence et les tuples de struct</span><span class="sxs-lookup"><span data-stu-id="7ba4e-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="7ba4e-139">Étant donné que les tuples de référence et les tuples de struct ont une représentation sous-jacente complètement différente, ils ne sont pas implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="7ba4e-140">Autrement dit, le code, tel que le suivant, n’est pas compilé:</span><span class="sxs-lookup"><span data-stu-id="7ba4e-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="7ba4e-141">Vous devez créer un modèle de correspondance sur un tuple et construire l’autre avec les parties constituantes.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="7ba4e-142">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7ba4e-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="7ba4e-143">Forme compilée de tuples de référence</span><span class="sxs-lookup"><span data-stu-id="7ba4e-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="7ba4e-144">Cette section explique la forme des tuples lorsqu’elles sont compilées.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="7ba4e-145">Les informations ici ne sont pas nécessaires pour la lecture, sauf si vous ciblez .NET Framework 3,5 ou une valeur inférieure.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="7ba4e-146">Les tuples sont compilés dans des objets de l’un des différents types `System.Tuple`génériques, tous nommés, qui sont surchargés sur l’arité, ou le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="7ba4e-147">Les types de tuples apparaissent dans ce formulaire lorsque vous les affichez à partir C# d’un autre langage, tel que ou Visual Basic, ou lorsque vous utilisez un F# outil qui n’est pas informé des constructions.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="7ba4e-148">Les `Tuple` types ont été introduits dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="7ba4e-149">Si vous ciblez une version antérieure du .NET Framework, le compilateur utilise les versions de [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) de la version 2,0 de la F# bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="7ba4e-150">Les types de cette bibliothèque sont utilisés uniquement pour les applications qui ciblent les versions 2,0, 3,0 et 3,5 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="7ba4e-151">Le transfert de type est utilisé pour garantir la compatibilité binaire entre les composants .NET Framework F# 2,0 et .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="7ba4e-152">Forme compilée de tuples de struct</span><span class="sxs-lookup"><span data-stu-id="7ba4e-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="7ba4e-153">Les tuples de struct (par `struct (x, y)`exemple,), sont fondamentalement différents des tuples de référence.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="7ba4e-154">Ils sont compilés dans <xref:System.ValueTuple> le type, surchargé par l’arité, ou le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="7ba4e-155">Ils sont équivalents aux [ C# tuples 7,0](../../csharp/tuples.md) et [Visual Basic 2017](../../visual-basic/programming-guide/language-features/data-types/tuples.md), et interagissent de manière bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="7ba4e-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ba4e-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ba4e-156">See also</span></span>

- [<span data-ttu-id="7ba4e-157">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="7ba4e-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7ba4e-158">Types F#</span><span class="sxs-lookup"><span data-stu-id="7ba4e-158">F# Types</span></span>](fsharp-types.md)
