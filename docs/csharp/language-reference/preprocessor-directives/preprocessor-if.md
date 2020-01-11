---
title: '#Directive de préprocesseur if - Référence C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899852"
---
# <a name="if-c-reference"></a><span data-ttu-id="aba8b-102">#if (C# référence)</span><span class="sxs-lookup"><span data-stu-id="aba8b-102">#if (C# reference)</span></span>

<span data-ttu-id="aba8b-103">Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini.</span><span class="sxs-lookup"><span data-stu-id="aba8b-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="aba8b-104">Contrairement à C et C++, vous ne pouvez pas attribuer de valeur numérique à un symbole.</span><span class="sxs-lookup"><span data-stu-id="aba8b-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="aba8b-105">L’instruction `#if` dans C# est booléenne et teste uniquement si le symbole a été défini ou non.</span><span class="sxs-lookup"><span data-stu-id="aba8b-105">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="aba8b-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="aba8b-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="aba8b-107">Vous pouvez utiliser les opérateurs [==](../operators/equality-operators.md#equality-operator-) (égalité) et [! =](../operators/equality-operators.md#inequality-operator-) (inégalité) uniquement pour tester les valeurs [bool](../builtin-types/bool.md) `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="aba8b-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="aba8b-108">`true` signifie que le symbole est défini.</span><span class="sxs-lookup"><span data-stu-id="aba8b-108">`true` means the symbol is defined.</span></span> <span data-ttu-id="aba8b-109">L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="aba8b-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="aba8b-110">Vous pouvez utiliser les [& & (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [ &#124; &#124; (ou)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)et [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) opérateurs permettant d’évaluer si plusieurs symboles ont été définis.</span><span class="sxs-lookup"><span data-stu-id="aba8b-110">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="aba8b-111">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="aba8b-111">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="aba8b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="aba8b-112">Remarks</span></span>

<span data-ttu-id="aba8b-113">`#if`, ainsi que les directives [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) et [#undef](preprocessor-undef.md), vous permettent d’inclure ou d’exclure du code en fonction de l’existence d’un ou plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="aba8b-113">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="aba8b-114">Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="aba8b-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="aba8b-115">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="aba8b-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="aba8b-116">`#define` vous permet de définir un symbole.</span><span class="sxs-lookup"><span data-stu-id="aba8b-116">`#define` lets you define a symbol.</span></span> <span data-ttu-id="aba8b-117">En utilisant ensuite ce dernier comme expression passée à la directive `#if`, l’expression correspond à `true`.</span><span class="sxs-lookup"><span data-stu-id="aba8b-117">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="aba8b-118">Vous pouvez aussi définir un symbole avec l’option du compilateur [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="aba8b-118">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="aba8b-119">Vous pouvez annuler la définition d’un symbole avec [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="aba8b-119">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="aba8b-120">Un symbole que vous définissez avec `-define` ou `#define` n’est pas en conflit avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="aba8b-120">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="aba8b-121">Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur, et un symbole ne peut être évalué que par une directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="aba8b-121">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="aba8b-122">La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.</span><span class="sxs-lookup"><span data-stu-id="aba8b-122">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="aba8b-123">Le système de génération est également conscient des symboles de préprocesseur prédéfinis qui représentent différents [frameworks cibles](../../../standard/frameworks.md) dans les projets de type SDK.</span><span class="sxs-lookup"><span data-stu-id="aba8b-123">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="aba8b-124">Ils sont utiles durant la création d’applications pouvant cibler plusieurs versions ou implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="aba8b-124">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="aba8b-125">Pour les projets de .NET Framework traditionnels, vous devez configurer manuellement les symboles de compilation conditionnelle pour les différents frameworks cibles dans Visual Studio via les pages de propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="aba8b-125">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="aba8b-126">Parmi les autres symboles prédéfinis se trouvent les constantes DEBUG et TRACE.</span><span class="sxs-lookup"><span data-stu-id="aba8b-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="aba8b-127">Vous pouvez remplacer les valeurs définies pour le projet à l’aide de `#define`.</span><span class="sxs-lookup"><span data-stu-id="aba8b-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="aba8b-128">Le symbole DEBUG, par exemple, est automatiquement défini en fonction de vos propriétés de configuration de build (mode « Debug » ou « Release »).</span><span class="sxs-lookup"><span data-stu-id="aba8b-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="aba8b-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="aba8b-129">Examples</span></span>

<span data-ttu-id="aba8b-130">L’exemple suivant montre comment définir un symbole MYTEST sur un fichier, puis tester les valeurs des symboles MYTEST et DEBUG.</span><span class="sxs-lookup"><span data-stu-id="aba8b-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="aba8b-131">La sortie de cet exemple dépend du mode de configuration que vous avez utilisé pour créer le projet (Debug ou Release).</span><span class="sxs-lookup"><span data-stu-id="aba8b-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="aba8b-132">L’exemple suivant montre comment tester différents frameworks cibles pour pouvoir utiliser les nouvelles API dans la mesure du possible :</span><span class="sxs-lookup"><span data-stu-id="aba8b-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aba8b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aba8b-133">See also</span></span>

- [<span data-ttu-id="aba8b-134">Référence C#</span><span class="sxs-lookup"><span data-stu-id="aba8b-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aba8b-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aba8b-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aba8b-136">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="aba8b-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="aba8b-137">Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="aba8b-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
