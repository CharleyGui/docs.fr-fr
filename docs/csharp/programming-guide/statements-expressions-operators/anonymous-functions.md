---
title: Fonctions anonymes - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711998"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="69f0d-102">Fonctions anonymes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="69f0d-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="69f0d-103">Une fonction anonyme est une instruction ou expression « inline » qui peut être utilisée partout où un type délégué est attendu.</span><span class="sxs-lookup"><span data-stu-id="69f0d-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="69f0d-104">Vous pouvez l’utiliser pour initialiser un délégué nommé ou la passer à la place d’un type délégué nommé comme paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="69f0d-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="69f0d-105">Vous pouvez utiliser une [expression lambda](lambda-expressions.md) ou une [méthode anonyme](../../language-reference/operators/delegate-operator.md) pour créer une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="69f0d-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="69f0d-106">Nous vous recommandons d’utiliser des expressions lambda, car elles fournissent un moyen plus concis et plus expressif d’écrire du code en ligne.</span><span class="sxs-lookup"><span data-stu-id="69f0d-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="69f0d-107">Contrairement aux méthodes anonymes, certains types d’expressions lambda peuvent être convertis en types d’arborescence d’expression.</span><span class="sxs-lookup"><span data-stu-id="69f0d-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="69f0d-108">Évolution des délégués en C\#</span><span class="sxs-lookup"><span data-stu-id="69f0d-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="69f0d-109">Dans C# 1.0, vous pouviez créer une instance d’un délégué en l’initialisant explicitement avec une méthode déjà définie à un autre endroit dans le code.</span><span class="sxs-lookup"><span data-stu-id="69f0d-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="69f0d-110">C# 2.0 a introduit le concept des méthodes anonymes, qui vous permettent d’écrire des blocs d’instructions inline sans nom pouvant être exécutés dans un appel de délégué.</span><span class="sxs-lookup"><span data-stu-id="69f0d-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="69f0d-111">C# 3.0 a introduit les expressions lambda, qui sont semblables aux méthodes anonymes d’un point de vue conceptuel, mais qui sont plus expressives et concises.</span><span class="sxs-lookup"><span data-stu-id="69f0d-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="69f0d-112">Ces deux fonctionnalités sont désignées collectivement comme des *fonctions anonymes*.</span><span class="sxs-lookup"><span data-stu-id="69f0d-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="69f0d-113">En général, les applications qui ciblent la version 3.5 ou une version ultérieure du .NET Framework utilisent des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="69f0d-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="69f0d-114">L’exemple suivant montre l’évolution de la création de délégués entre C# 1.0 et C# 3.0 :</span><span class="sxs-lookup"><span data-stu-id="69f0d-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="69f0d-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="69f0d-115">C# language specification</span></span>

<span data-ttu-id="69f0d-116">Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="69f0d-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="69f0d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69f0d-117">See also</span></span>

- [<span data-ttu-id="69f0d-118">Instructions, expressions et opérateurs</span><span class="sxs-lookup"><span data-stu-id="69f0d-118">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="69f0d-119">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="69f0d-119">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="69f0d-120">Délégués</span><span class="sxs-lookup"><span data-stu-id="69f0d-120">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="69f0d-121">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="69f0d-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
