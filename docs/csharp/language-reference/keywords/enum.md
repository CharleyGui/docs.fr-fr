---
title: enum, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 6af1f7f23447f9f1379ac6d223e198a4a2ea5645
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424244"
---
# <a name="enum-c-reference"></a><span data-ttu-id="0a824-102">enum (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0a824-102">enum (C# Reference)</span></span>

<span data-ttu-id="0a824-103">Le mot clé `enum` est utilisé pour déclarer une énumération. Il s’agit d’un type distinct qui se compose d’un ensemble de constantes nommées, appelé liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="0a824-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  

<span data-ttu-id="0a824-104">Il est généralement préférable de définir une énumération directement dans un espace de noms pour que toutes les classes de l’espace de noms puissent y accéder avec la même facilité.</span><span class="sxs-lookup"><span data-stu-id="0a824-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="0a824-105">Toutefois, une énumération peut également être imbriquée dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="0a824-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="0a824-106">Par défaut, le premier énumérateur a la valeur 0 et chaque énumérateur successif est augmenté de 1.</span><span class="sxs-lookup"><span data-stu-id="0a824-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="0a824-107">Par exemple, dans l’énumération suivante, `Sat` est `0`, `Sun` est `1`, `Mon` est `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0a824-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="0a824-108">Les énumérateurs peuvent utiliser des initialiseurs pour remplacer les valeurs par défaut, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0a824-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="0a824-109">Dans cette énumération, le début de la séquence des éléments est forcé à `1` au lieu de `0`.</span><span class="sxs-lookup"><span data-stu-id="0a824-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="0a824-110">Il est cependant recommandé d’inclure une constante qui a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="0a824-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="0a824-111">Pour plus d’informations, consultez [Types énumération](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a824-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="0a824-112">Chaque type énumération a un type sous-jacent qui peut correspondre à n’importe quel [type numérique intégral](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a824-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="0a824-113">Le type [char](char.md) ne peut pas être un type sous-jacent d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="0a824-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="0a824-114">Le type sous-jacent par défaut des éléments de l’énumération est [int](../builtin-types/integral-numeric-types.md). Pour déclarer une énumération d’un autre type intégral, comme [byte](../builtin-types/integral-numeric-types.md), utilisez un signe deux-points après l’identificateur, suivi du type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0a824-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```


<span data-ttu-id="0a824-115">Une variable de type énumération peut avoir n’importe quelle valeur de la plage du type sous-jacent ; les valeurs ne sont pas limitées aux constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="0a824-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="0a824-116">La valeur par défaut de `enum E` est la valeur produite par l’expression `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="0a824-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="0a824-117">Le nom d’un énumérateur ne peut pas contenir d’espaces.</span><span class="sxs-lookup"><span data-stu-id="0a824-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="0a824-118">Le type sous-jacent spécifie la quantité de stockage allouée pour chaque énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0a824-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="0a824-119">Cependant, un cast explicite est nécessaire pour convertir du type `enum` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="0a824-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="0a824-120">Par exemple, l’instruction suivante affecte l’énumérateur `Sun` à une variable du type [int](../builtin-types/integral-numeric-types.md) en utilisant un cast pour convertir de `enum` en `int`.</span><span class="sxs-lookup"><span data-stu-id="0a824-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="0a824-121">Quand vous appliquez <xref:System.FlagsAttribute?displayProperty=nameWithType> à une énumération qui contient des éléments qui peuvent être combinés avec une opération `OR` au niveau du bit, l’attribut affecte le comportement d’ `enum` quand elle est utilisée avec certains outils.</span><span class="sxs-lookup"><span data-stu-id="0a824-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="0a824-122">Vous pouvez remarquer ces modifications quand vous utilisez des outils comme les méthodes de la classe <xref:System.Console> et l’évaluateur d’expression.</span><span class="sxs-lookup"><span data-stu-id="0a824-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="0a824-123">(Voir le troisième exemple.)</span><span class="sxs-lookup"><span data-stu-id="0a824-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="0a824-124">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="0a824-124">Robust programming</span></span>

<span data-ttu-id="0a824-125">Tout comme avec n’importe quelle constante, toutes les références aux valeurs individuelles d’une énumération sont converties en littéraux numériques au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="0a824-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="0a824-126">Cette opération peut créer des problèmes potentiels de gestion de version, comme décrit dans [Constantes](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="0a824-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="0a824-127">L’affectation de valeurs supplémentaires à de nouvelles versions d’énumérations ou la modification des valeurs des membres d’une énumération dans une nouvelle version peut entraîner des problèmes pour le code source dépendant.</span><span class="sxs-lookup"><span data-stu-id="0a824-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="0a824-128">Les valeurs des énumérations sont souvent utilisées dans des instructions [switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="0a824-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="0a824-129">Si des éléments supplémentaires ont été ajoutées au type `enum` , la section par défaut de l’instruction switch peut être sélectionnée de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="0a824-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="0a824-130">Si d’autres développeurs utilisent votre code, vous devez fournir des instructions sur la manière dont leur code doit réagir si de nouveaux éléments sont ajoutés à des types `enum` .</span><span class="sxs-lookup"><span data-stu-id="0a824-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="0a824-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="0a824-131">Example</span></span>

<span data-ttu-id="0a824-132">Dans l’exemple suivant, une énumération, `Day`, est déclarée.</span><span class="sxs-lookup"><span data-stu-id="0a824-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="0a824-133">Deux énumérateurs sont explicitement convertis en entiers et affectés à des variables entières.</span><span class="sxs-lookup"><span data-stu-id="0a824-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="0a824-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="0a824-134">Example</span></span>

<span data-ttu-id="0a824-135">Dans l’exemple suivant, l’option de type de base est utilisée pour déclarer une `enum` dont les membres sont de type `long`.</span><span class="sxs-lookup"><span data-stu-id="0a824-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="0a824-136">Notez que même si le type sous-jacent de l’énumération est `long`, les membres de l’énumération doivent toujours être explicitement convertis en type `long` en utilisant un cast.</span><span class="sxs-lookup"><span data-stu-id="0a824-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="0a824-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="0a824-137">Example</span></span>

<span data-ttu-id="0a824-138">L’exemple de code suivant montre l’utilisation et l’effet de l’attribut <xref:System.FlagsAttribute?displayProperty=nameWithType> sur une déclaration `enum` .</span><span class="sxs-lookup"><span data-stu-id="0a824-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="0a824-139">Commentaires</span><span class="sxs-lookup"><span data-stu-id="0a824-139">Comments</span></span>

<span data-ttu-id="0a824-140">Si vous supprimez `Flags`, l’exemple affiche les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a824-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="0a824-141">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0a824-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0a824-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a824-142">See also</span></span>

- [<span data-ttu-id="0a824-143">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0a824-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0a824-144">Types d’énumération</span><span class="sxs-lookup"><span data-stu-id="0a824-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="0a824-145">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="0a824-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0a824-146">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="0a824-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="0a824-147">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="0a824-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="0a824-148">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="0a824-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="0a824-149">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="0a824-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="0a824-150">Conventions de nommage des énumérations</span><span class="sxs-lookup"><span data-stu-id="0a824-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
