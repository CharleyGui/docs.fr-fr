---
title: Types référence intégrés - Référence C#
description: Découvrez les types référence qui ont des mots clés C# que vous pouvez utiliser pour les déclarer.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223517"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="3f9c1-103">Types référence intégrés (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="3f9c1-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="3f9c1-104">C# a un nombre de types référence intégrés.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="3f9c1-105">Ils ont des mots clés ou des opérateurs qui sont synonymes pour un type dans la bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span>

## <a name="the-object-type"></a><span data-ttu-id="3f9c1-106">Type d’objet.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-106">The object type</span></span>

<span data-ttu-id="3f9c1-107">Le type `object` est un alias de <xref:System.Object?displayProperty=nameWithType> dans .NET.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="3f9c1-108">Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f9c1-109">Vous pouvez assigner des valeurs de tout type aux variables de type `object`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="3f9c1-110">Toute variable `object` peut être attribuée à sa valeur par défaut à l’aide du littéral `null`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="3f9c1-111">Quand une variable d’un type valeur est convertie en type objet, elle est dite *boxed*.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="3f9c1-112">Quand une variable de type `object` est convertie en un type valeur, elle est dite *unboxed*.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="3f9c1-113">Pour plus d’informations, consultez [Conversion boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c1-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="the-string-type"></a><span data-ttu-id="3f9c1-114">Type de chaîne</span><span class="sxs-lookup"><span data-stu-id="3f9c1-114">The string type</span></span>

<span data-ttu-id="3f9c1-115">Le type `string` représente une séquence de zéro, un ou plusieurs caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="3f9c1-116">`string` est un alias de <xref:System.String?displayProperty=nameWithType> dans .NET.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="3f9c1-117">Bien que `string` soit un type référence, les [opérateurs d’égalité`==` (`!=` et ](../operators/equality-operators.md#string-equality)) sont définis pour comparer les valeurs des objets `string`, pas les références.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="3f9c1-118">Cela permet de tester l’égalité de chaînes de façon plus intuitive.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="3f9c1-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="3f9c1-120">Cette opération affiche « True », puis « False », car le contenu des chaînes est équivalent, mais `a` et `b` ne font pas référence à la même instance de chaîne.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="3f9c1-121">L’[opérateur +](../operators/addition-operator.md#string-concatenation) concatène les chaînes :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="3f9c1-122">Cela crée un objet String qui contient « good morning ».</span><span class="sxs-lookup"><span data-stu-id="3f9c1-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="3f9c1-123">Les chaînes sont *immuables* : il est impossible de changer le contenu d’un objet String après avoir créé l’objet, bien que la syntaxe semble indiquer le contraire.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="3f9c1-124">Par exemple, lorsque vous écrivez ce code, le compilateur crée en fait un nouvel objet String pour stocker la nouvelle séquence de caractères, et ce nouvel objet est attribué à `b`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="3f9c1-125">La mémoire allouée pour `b` (quand elle contenait la chaîne « h ») est alors éligible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="3f9c1-126">L' `[]` [opérateur](../operators/member-access-operators.md#indexer-operator-) peut être utilisé pour l’accès en lecture seule aux caractères individuels d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="3f9c1-127">Les valeurs d’index valides commencent à `0` et doivent être inférieures à la longueur de la chaîne :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="3f9c1-128">De la même façon, l' `[]` opérateur peut également être utilisé pour effectuer une itération au sein de chaque caractère dans une chaîne :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

<span data-ttu-id="3f9c1-129">Les littéraux de chaîne sont de type `string` et peuvent être écrits sous deux formes, entre guillemets et entre `@`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="3f9c1-130">Les littéraux de chaîne entre guillemets sont placés entre guillemets doubles (") :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="3f9c1-131">Les littéraux de chaîne peuvent contenir tout littéral de caractère.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-131">String literals can contain any character literal.</span></span> <span data-ttu-id="3f9c1-132">Les séquences d’échappement sont incluses.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-132">Escape sequences are included.</span></span> <span data-ttu-id="3f9c1-133">L’exemple suivant utilise la séquence d’échappement `\\` pour la barre oblique inverse, `\u0066` pour la lettre f et `\n` pour un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> <span data-ttu-id="3f9c1-134">Le code d’échappement `\udddd` (où `dddd` est un nombre à quatre chiffres) représente le caractère Unicode U+`dddd`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="3f9c1-135">Les codes d’échappement Unicode à huit chiffres sont également reconnus : `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="3f9c1-136">Les [littéraux de chaîne textuelle](../tokens/verbatim.md) commencent par `@` et sont placés entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="3f9c1-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="3f9c1-138">L’avantage des chaînes textuelles est que les séquences d’échappement *ne sont pas* traitées, ce qui facilite l’écriture, par exemple, d’un nom de fichier complet Windows :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="3f9c1-139">Pour inclure un guillemet double dans une chaîne @-quoted, doublez-le :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="3f9c1-140">Type de délégué</span><span class="sxs-lookup"><span data-stu-id="3f9c1-140">The delegate type</span></span>

<span data-ttu-id="3f9c1-141">La déclaration d’un type délégué est semblable à une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="3f9c1-142">Elle a une valeur de retour et un nombre quelconque de paramètres de type quelconque :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="3f9c1-143">Dans .NET, les types `System.Action` et `System.Func` fournissent des définitions génériques pour de nombreux délégués courants.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="3f9c1-144">Vous n’avez probablement pas besoin de définir de nouveaux types de délégué personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="3f9c1-145">À la place, vous pouvez créer des instanciations des types génériques fournis.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="3f9c1-146">Un `delegate` est un type référence qui peut être utilisé pour encapsuler une méthode anonyme ou nommée.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="3f9c1-147">Les délégués sont comparables aux pointeurs fonction en C++, mais ils offrent l’avantage d’être sûrs et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="3f9c1-148">Pour les applications de délégués, consultez [Délégués](../../programming-guide/delegates/index.md) et [Délégués génériques](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c1-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="3f9c1-149">Les délégués sont la base des [événements](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c1-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="3f9c1-150">Un délégué peut être instancié en l’associant à une méthode nommée ou anonyme.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="3f9c1-151">Le délégué doit être instancié avec une méthode ou une expression lambda qui a un type de retour compatible et des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="3f9c1-152">Pour plus d’informations sur le degré de variance autorisé dans la signature de méthode, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c1-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="3f9c1-153">Pour une utilisation avec des méthodes anonymes, le délégué et le code à lui associer sont déclarés ensemble.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span>

## <a name="the-dynamic-type"></a><span data-ttu-id="3f9c1-154">Type dynamique</span><span class="sxs-lookup"><span data-stu-id="3f9c1-154">The dynamic type</span></span>

<span data-ttu-id="3f9c1-155">Le type `dynamic` indique que l’utilisation de la variable et des références à ses membres contourne la vérification du type au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="3f9c1-156">Au lieu de cela, ces opérations sont résolues au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="3f9c1-157">Le type `dynamic` simplifie l’accès aux API COM telles que les API Office Automation, aux API dynamiques telles que les bibliothèques IronPython et au modèle DOM (Document Object Model) HTML.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="3f9c1-158">Le type `dynamic` se comporte comme le type `object` dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="3f9c1-159">En particulier, toute expression non null peut être convertie en type `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="3f9c1-160">Le type `dynamic` diffère de `object` en cela que les opérations qui contiennent des expressions de type `dynamic` ne sont pas résolues et leur type n’est pas vérifié par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="3f9c1-161">Le compilateur empaquète des informations sur l’opération, qui sont ensuite utilisées pour évaluer l’opération au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="3f9c1-162">Dans le cadre du processus, les variables de type `dynamic` sont compilées dans des variables de type `object`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="3f9c1-163">Ainsi, le type `dynamic` existe seulement au moment de la compilation, et non au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="3f9c1-164">L’exemple suivant compare une variable de type `dynamic` à une variable de type `object`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="3f9c1-165">Pour vérifier le type de chaque variable au moment de la compilation, placez le pointeur de la souris sur `dyn` ou `obj` dans les instructions `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="3f9c1-166">Copiez le code suivant dans un éditeur où IntelliSense est disponible.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="3f9c1-167">IntelliSense affiche **dynamic** pour `dyn` et **object** pour `obj`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="3f9c1-168">Les instructions <xref:System.Console.WriteLine%2A> affichent les types d’exécution de `dyn` et `obj`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="3f9c1-169">À ce stade, tous deux ont le même type, entier.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="3f9c1-170">La sortie suivante est produite :</span><span class="sxs-lookup"><span data-stu-id="3f9c1-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="3f9c1-171">Pour voir la différence entre `dyn` et `obj` au moment de la compilation, ajoutez les deux lignes suivantes entre les déclarations et les instructions `WriteLine` de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="3f9c1-172">Une erreur du compilateur est signalée pour la tentative d’ajout d’un entier et un d’objet dans l’expression `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="3f9c1-173">Toutefois, aucune erreur n’est signalée pour `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="3f9c1-174">L’expression qui contient `dyn` n’est pas vérifié au moment de la compilation, car le type de `dyn` est `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="3f9c1-175">L’exemple suivant utilise `dynamic` dans plusieurs déclarations.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="3f9c1-176">La méthode `Main` compare également la vérification de type au moment de la compilation avec la vérification de type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f9c1-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="3f9c1-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f9c1-177">See also</span></span>

- [<span data-ttu-id="3f9c1-178">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3f9c1-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f9c1-179">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3f9c1-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3f9c1-180">Événements</span><span class="sxs-lookup"><span data-stu-id="3f9c1-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="3f9c1-181">Utilisation du type dynamic</span><span class="sxs-lookup"><span data-stu-id="3f9c1-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="3f9c1-182">Meilleures pratiques pour l’utilisation de chaînes</span><span class="sxs-lookup"><span data-stu-id="3f9c1-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="3f9c1-183">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="3f9c1-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="3f9c1-184">Création de chaînes</span><span class="sxs-lookup"><span data-stu-id="3f9c1-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="3f9c1-185">Opérateurs de conversion et de test de type</span><span class="sxs-lookup"><span data-stu-id="3f9c1-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="3f9c1-186">Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs As et is</span><span class="sxs-lookup"><span data-stu-id="3f9c1-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="3f9c1-187">Procédure pas à pas : création et utilisation d’objets dynamiques</span><span class="sxs-lookup"><span data-stu-id="3f9c1-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
