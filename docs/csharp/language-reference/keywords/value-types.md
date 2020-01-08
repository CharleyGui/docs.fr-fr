---
title: Types valeur - Référence C#
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 31563eccd50e6acd27a8e5a4ee96046fd2728695
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345357"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="a0fde-102">Types valeur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a0fde-102">Value types (C# Reference)</span></span>

<span data-ttu-id="a0fde-103">Il existe deux sortes de types valeur :</span><span class="sxs-lookup"><span data-stu-id="a0fde-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="a0fde-104">Structures</span><span class="sxs-lookup"><span data-stu-id="a0fde-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="a0fde-105">Énumérations</span><span class="sxs-lookup"><span data-stu-id="a0fde-105">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="a0fde-106">Principales caractéristiques des types valeur</span><span class="sxs-lookup"><span data-stu-id="a0fde-106">Main features of value types</span></span>

<span data-ttu-id="a0fde-107">Une variable d’un type valeur contient une valeur du type.</span><span class="sxs-lookup"><span data-stu-id="a0fde-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="a0fde-108">Par exemple, une variable du type `int` peut contenir la valeur `42`.</span><span class="sxs-lookup"><span data-stu-id="a0fde-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="a0fde-109">Ce type s’oppose au type référence, qui contient une référence à une instance du type, également appelée objet.</span><span class="sxs-lookup"><span data-stu-id="a0fde-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="a0fde-110">Lorsque vous affectez une nouvelle valeur à une variable d’un type valeur, cette valeur est copiée.</span><span class="sxs-lookup"><span data-stu-id="a0fde-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="a0fde-111">Si vous affectez une nouvelle valeur à une variable d’un type référence, la référence est copiée, et non l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="a0fde-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="a0fde-112">Tous les types valeur sont implicitement dérivés de <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0fde-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a0fde-113">Contrairement aux types référence, vous ne pouvez pas faire dériver un nouveau type d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="a0fde-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="a0fde-114">En revanche, comme les types référence, les structs peuvent implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="a0fde-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="a0fde-115">Les variables de type valeur ne peut pas être `null` par défaut.</span><span class="sxs-lookup"><span data-stu-id="a0fde-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="a0fde-116">Toutefois, les variables des [types valeur Nullable](../builtin-types/nullable-value-types.md) correspondants peuvent être `null`.</span><span class="sxs-lookup"><span data-stu-id="a0fde-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span></span>

<span data-ttu-id="a0fde-117">Chaque type valeur a un constructeur implicite sans paramètre qui initialise la valeur par défaut de ce type.</span><span class="sxs-lookup"><span data-stu-id="a0fde-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="a0fde-118">Pour plus d’informations sur les valeurs par défaut des types valeur, voir [Tableau des valeurs par défaut](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="a0fde-119">Types simples</span><span class="sxs-lookup"><span data-stu-id="a0fde-119">Simple types</span></span>

<span data-ttu-id="a0fde-120">Les *types simples* sont un ensemble de types struct prédéfinis fournis par C#, composé des types suivants :</span><span class="sxs-lookup"><span data-stu-id="a0fde-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="a0fde-121">[Types intégraux](../builtin-types/integral-numeric-types.md) : types numériques entiers et type [char](../builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="a0fde-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](../builtin-types/char.md) type</span></span>
- [<span data-ttu-id="a0fde-122">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="a0fde-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="a0fde-123">bool</span><span class="sxs-lookup"><span data-stu-id="a0fde-123">bool</span></span>](../builtin-types/bool.md)

<span data-ttu-id="a0fde-124">Les types simples sont identifiés par des mots clés, qui sont simplement des alias de types struct prédéfinis dans l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="a0fde-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="a0fde-125">Par exemple, [int](../builtin-types/integral-numeric-types.md) est un alias de <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0fde-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0fde-126">Pour connaître la liste complète des alias, voir [Tableau des types intégrés](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="a0fde-127">Les types simples diffèrent des autres types struct en ce qu’ils autorisent des opérations supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="a0fde-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="a0fde-128">Les types simples peuvent être initialisés à l’aide de littéraux.</span><span class="sxs-lookup"><span data-stu-id="a0fde-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="a0fde-129">Par exemple, `'A'` est un littéral de type `char`, tandis que `2001` est un littéral de type `int`.</span><span class="sxs-lookup"><span data-stu-id="a0fde-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="a0fde-130">Vous pouvez déclarer des constantes des types simples avec le mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="a0fde-131">Il n’est pas possible d’avoir des constantes d’autres types struct.</span><span class="sxs-lookup"><span data-stu-id="a0fde-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="a0fde-132">Les expressions constantes, dont les opérandes sont tous des constantes de type simple, sont évaluées au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a0fde-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="a0fde-133">Pour plus d’informations, voir la section [Types simples](~/_csharplang/spec/types.md#simple-types) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a0fde-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="a0fde-134">Initialiser des types valeur</span><span class="sxs-lookup"><span data-stu-id="a0fde-134">Initializing value types</span></span>

<span data-ttu-id="a0fde-135">En C#, les variables locales doivent être initialisées avant d’être utilisées.</span><span class="sxs-lookup"><span data-stu-id="a0fde-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="a0fde-136">Par exemple, vous pouvez déclarer une variable locale sans l’initialiser comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a0fde-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="a0fde-137">Vous ne pouvez pas l’utiliser avant de l’avoir initialisée.</span><span class="sxs-lookup"><span data-stu-id="a0fde-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="a0fde-138">Vous pouvez l’initialiser à l’aide de l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="a0fde-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="a0fde-139">Cette instruction est équivalente à l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="a0fde-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="a0fde-140">Bien entendu, vous pouvez intégrer la déclaration et l’initialisation dans une même instruction comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="a0fde-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="a0fde-141">– ou –</span><span class="sxs-lookup"><span data-stu-id="a0fde-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="a0fde-142">L’opérateur [new](../operators/new-operator.md) permet d’appeler le constructeur sans paramètre du type spécifique et d’affecter la valeur par défaut à la variable.</span><span class="sxs-lookup"><span data-stu-id="a0fde-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="a0fde-143">Dans l’exemple précédent, le constructeur sans paramètre a affecté la valeur `0` à `myInt`.</span><span class="sxs-lookup"><span data-stu-id="a0fde-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="a0fde-144">Pour plus d’informations sur les valeurs affectées en appelant les constructeurs sans paramètre, voir [Tableau des valeurs par défaut](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="a0fde-145">Avec les types définis par l’utilisateur, l’opérateur [new](../operators/new-operator.md) permet d’appeler le constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="a0fde-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="a0fde-146">Par exemple, l’instruction suivante appelle le constructeur sans paramètre du struct `Point` :</span><span class="sxs-lookup"><span data-stu-id="a0fde-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="a0fde-147">Après cet appel, le struct est considéré comme définitivement assigné ; autrement dit, tous ses membres sont initialisés avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a0fde-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="a0fde-148">Pour plus d'informations sur l'opérateur `new`, voir [new](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="a0fde-149">Pour plus d’informations sur la mise en forme de la sortie des types numériques, voir [Tableau des formats des résultats numériques](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="a0fde-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0fde-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0fde-150">See also</span></span>

- [<span data-ttu-id="a0fde-151">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="a0fde-151">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a0fde-152">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a0fde-152">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a0fde-153">Types référence</span><span class="sxs-lookup"><span data-stu-id="a0fde-153">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="a0fde-154">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="a0fde-154">Nullable value types</span></span>](../builtin-types/nullable-value-types.md)
