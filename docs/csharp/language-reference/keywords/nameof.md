---
title: nameof - Référence C#
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 349cbf4e918d97a5a2a5c1e873d7fa114be8e2db
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306631"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="7b9b5-102">nameof (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="7b9b5-102">nameof (C# Reference)</span></span>

<span data-ttu-id="7b9b5-103">Permet d'obtenir le nom de chaîne simple (non qualifié) d'une variable, d'un type ou d'un membre.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>

<span data-ttu-id="7b9b5-104">Pour le signalement des erreurs dans le code, le raccordement aux liens MVC (model-view-controller) et le déclenchement des événements de modification de propriété, entre autres, il est souvent utile de capturer le nom de chaîne d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="7b9b5-105">L'utilisation de `nameof` vous aide à garantir la validité de votre code quand vous renommez des définitions.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="7b9b5-106">Auparavant, vous deviez utiliser des littéraux de chaîne pour faire référence aux définitions, ce qui présentait un risque quand vous renommiez des éléments de code, car les outils ne vérifiaient pas ces littéraux de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>

<span data-ttu-id="7b9b5-107">Une expression `nameof` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-107">A `nameof` expression has this form:</span></span>

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a><span data-ttu-id="7b9b5-108">Principaux cas d'usage</span><span class="sxs-lookup"><span data-stu-id="7b9b5-108">Key Use Cases</span></span>

<span data-ttu-id="7b9b5-109">Ces exemples montrent les principaux cas d'usage de `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-109">These examples show the key use cases for `nameof`.</span></span>

<span data-ttu-id="7b9b5-110">Validation des paramètres :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-110">Validate parameters:</span></span>

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

<span data-ttu-id="7b9b5-111">Liens d'action MVC :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-111">MVC Action links:</span></span>

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

<span data-ttu-id="7b9b5-112">INotifyPropertyChanged :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-112">INotifyPropertyChanged:</span></span>

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

<span data-ttu-id="7b9b5-113">Propriété de dépendance XAML :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-113">XAML dependency property:</span></span>

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

<span data-ttu-id="7b9b5-114">Journalisation :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-114">Logging:</span></span>

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

<span data-ttu-id="7b9b5-115">Attributs :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-115">Attributes:</span></span>

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a><span data-ttu-id="7b9b5-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="7b9b5-116">Examples</span></span>

<span data-ttu-id="7b9b5-117">Exemples C# :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-117">Some C# examples:</span></span>

```csharp
using Stuff = Some.Cool.Functionality
class C {
    static int Method1 (string x, int y) {}
    static int Method1 (string x, string y) {}
    int Method2 (int z) {}
    string f<T>() => nameof(T);
}

var c = new C()

class Test {
    static void Main (string[] args) {
        Console.WriteLine(nameof(C)); // -> "C"
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]
        Console.WriteLine(nameof(f)); // -> "f"
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]
        // Console.WriteLine(nameof(f<>)); -> [syntax error]
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]
    }
}
```

## <a name="remarks"></a><span data-ttu-id="7b9b5-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b9b5-118">Remarks</span></span>

<span data-ttu-id="7b9b5-119">L'argument de `nameof` doit être un nom simple, un nom qualifié, un accès au membre, un accès de base avec un membre spécifié ou cet accès avec un membre spécifié.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="7b9b5-120">L'expression d'argument identifie une définition de code, mais n'est jamais évaluée.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>

<span data-ttu-id="7b9b5-121">L'argument doit être une expression d'un point de vue syntaxique. Il existe donc beaucoup d'éléments non autorisés qu'il n'est pas utile de répertorier ici.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="7b9b5-122">En revanche, nous mentionnerons les éléments suivants qui génèrent des erreurs : les types prédéfinis (par exemple, `int` ou `void`), les types Nullable (`Point?`), les types tableau (`Customer[,]`), les types pointeur (`Buffer*`), les alias qualifiés (`A::B`), les types génériques indépendants (`Dictionary<,>`), les symboles de prétraitement (`DEBUG`) et les étiquettes (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="7b9b5-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>

<span data-ttu-id="7b9b5-123">Si vous avez besoin d'obtenir le nom qualifié complet, vous pouvez utiliser l'expression `typeof` avec `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="7b9b5-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-124">For example:</span></span>

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

<span data-ttu-id="7b9b5-125">Malheureusement, `typeof` n’est pas une expression constante comme `nameof`, `typeof` ne peut donc pas être utilisé en conjonction avec `nameof` dans les mêmes emplacements que `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="7b9b5-126">Par exemple, le code suivant entraîne une erreur de compilation CS0182 :</span><span class="sxs-lookup"><span data-stu-id="7b9b5-126">For example, the following would cause a CS0182 compile error:</span></span>

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

<span data-ttu-id="7b9b5-127">Les exemples montrent que vous pouvez utiliser un nom de type et accéder à un nom de méthode d'instance.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="7b9b5-128">Il n'est pas nécessaire d'avoir une instance du type, comme c'est le cas dans les expressions évaluées.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="7b9b5-129">Utiliser le nom de type peut être très pratique dans certains cas et, comme vous référencez seulement le nom et que vous n'utilisez pas de données d'instance, vous n'avez pas besoin de combiner une variable d'instance ou une expression.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>

<span data-ttu-id="7b9b5-130">Vous pouvez référencer les membres d'une classe dans les expressions d'attribut sur la classe.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-130">You can reference the members of a class in attribute expressions on the class.</span></span>

<span data-ttu-id="7b9b5-131">Il n'existe aucun moyen pour obtenir des informations de signature comme « `Method1 (str, str)` ».</span><span class="sxs-lookup"><span data-stu-id="7b9b5-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="7b9b5-132">Pour cela, vous pouvez utiliser une expression, `Expression e = () => A.B.Method1("s1", "s2")`, puis extraire MemberInfo de l'arborescence de l'expression qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="7b9b5-133">Spécifications du langage</span><span class="sxs-lookup"><span data-stu-id="7b9b5-133">Language Specifications</span></span>

<span data-ttu-id="7b9b5-134">Pour plus d’informations, consultez [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b9b5-134">For more information, see [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="7b9b5-135">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="7b9b5-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b9b5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b9b5-136">See also</span></span>

- [<span data-ttu-id="7b9b5-137">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7b9b5-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7b9b5-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7b9b5-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7b9b5-139">typeof</span><span class="sxs-lookup"><span data-stu-id="7b9b5-139">typeof</span></span>](../operators/type-testing-and-conversion-operators.md#typeof-operator)
