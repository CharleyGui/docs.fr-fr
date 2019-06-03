---
title: '#Directive de préprocesseur if - Référence C#'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 12ef0926665103e739ed4a8ee83ff895b439fffc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300073"
---
# <a name="if-c-reference"></a><span data-ttu-id="4c725-102">#if (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4c725-102">#if (C# Reference)</span></span>

<span data-ttu-id="4c725-103">Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini.</span><span class="sxs-lookup"><span data-stu-id="4c725-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="4c725-104">Contrairement à C et C++, vous ne pouvez pas attribuer de valeur numérique à un symbole.</span><span class="sxs-lookup"><span data-stu-id="4c725-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="4c725-105">L’instruction #if en C# est booléenne et teste uniquement si le symbole a été défini ou non.</span><span class="sxs-lookup"><span data-stu-id="4c725-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="4c725-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4c725-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="4c725-107">Vous pouvez utiliser les opérateurs [==](../operators/equality-operators.md#equality-operator-) (égalité) et [!=](../operators/equality-operators.md#inequality-operator-) (inégalité) uniquement pour tester la valeur [true](../keywords/true-literal.md) ou [false](../keywords/false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4c725-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="4c725-108">True signifie que le symbole est défini.</span><span class="sxs-lookup"><span data-stu-id="4c725-108">True means the symbol is defined.</span></span> <span data-ttu-id="4c725-109">L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="4c725-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="4c725-110">Vous pouvez utiliser les opérateurs [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (et), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or) et [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="4c725-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="4c725-111">(not) pour vérifier si plusieurs symboles ont été définis.</span><span class="sxs-lookup"><span data-stu-id="4c725-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="4c725-112">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4c725-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c725-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="4c725-113">Remarks</span></span>

<span data-ttu-id="4c725-114">`#if`, ainsi que les directives [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) et [#undef](preprocessor-undef.md), vous permettent d’inclure ou d’exclure du code en fonction de l’existence d’un ou plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="4c725-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="4c725-115">Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c725-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="4c725-116">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="4c725-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="4c725-117">`#define` vous permet de définir un symbole.</span><span class="sxs-lookup"><span data-stu-id="4c725-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="4c725-118">En utilisant ensuite ce dernier comme expression passée à la directive `#if`, l’expression correspond à `true`.</span><span class="sxs-lookup"><span data-stu-id="4c725-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="4c725-119">Vous pouvez aussi définir un symbole avec l’option du compilateur [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4c725-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="4c725-120">Vous pouvez annuler la définition d’un symbole avec [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="4c725-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="4c725-121">Un symbole que vous définissez avec `-define` ou `#define` n’est pas en conflit avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="4c725-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="4c725-122">Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur, et un symbole ne peut être évalué que par une directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="4c725-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="4c725-123">La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.</span><span class="sxs-lookup"><span data-stu-id="4c725-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="4c725-124">Le système de génération tient également compte des symboles de préprocesseur prédéfinis représentant différents [frameworks cibles](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4c725-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="4c725-125">Ils sont utiles durant la création d’applications pouvant cibler plusieurs versions ou implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="4c725-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="4c725-126">Parmi les autres symboles prédéfinis se trouvent les constantes DEBUG et TRACE.</span><span class="sxs-lookup"><span data-stu-id="4c725-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="4c725-127">Vous pouvez remplacer les valeurs définies pour le projet à l’aide de `#define`.</span><span class="sxs-lookup"><span data-stu-id="4c725-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="4c725-128">Le symbole DEBUG, par exemple, est automatiquement défini en fonction de vos propriétés de configuration de build (mode « Debug » ou « Release »).</span><span class="sxs-lookup"><span data-stu-id="4c725-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="4c725-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="4c725-129">Examples</span></span>

<span data-ttu-id="4c725-130">L’exemple suivant montre comment définir un symbole MYTEST sur un fichier, puis tester les valeurs des symboles MYTEST et DEBUG.</span><span class="sxs-lookup"><span data-stu-id="4c725-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="4c725-131">La sortie de cet exemple dépend du mode de configuration que vous avez utilisé pour créer le projet (Debug ou Release).</span><span class="sxs-lookup"><span data-stu-id="4c725-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="4c725-132">L’exemple suivant montre comment tester différents frameworks cibles pour pouvoir utiliser les nouvelles API dans la mesure du possible :</span><span class="sxs-lookup"><span data-stu-id="4c725-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="4c725-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c725-133">See also</span></span>

- [<span data-ttu-id="4c725-134">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4c725-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4c725-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4c725-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4c725-136">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="4c725-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="4c725-137">Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="4c725-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
