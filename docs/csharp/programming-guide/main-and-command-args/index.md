---
title: Main() et arguments de ligne de commande - Guide de programmation C#
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 5de7e565560928b1867ba96c8937fd354c276806
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774123"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="bd5a1-102">Main() et arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a1-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="bd5a1-103">La méthode `Main` est le point d’entrée d’une application C#.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="bd5a1-104">(Les bibliothèques et les services ne requièrent pas de méthode `Main` comme point d’entrée.) Lorsque l’application est démarrée, la méthode `Main` est la première méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="bd5a1-105">Il ne peut y avoir qu’un seul point d’entrée dans un programme C#.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="bd5a1-106">Si plusieurs classes ont une méthode `Main`, vous devez compiler votre programme avec l’option de compilateur **/main** pour spécifier quelle méthode `Main` utiliser comme point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="bd5a1-107">Pour plus d’informations, consultez [-mainC# (options du compilateur)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a1-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="bd5a1-108">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="bd5a1-108">Overview</span></span>

- <span data-ttu-id="bd5a1-109">La méthode `Main` est le point d’entrée d’un programme exécutable ; c’est l’endroit où le contrôle du programme commence et se termine.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="bd5a1-110">`Main` est déclaré à l’intérieur d’une classe ou d’un struct.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="bd5a1-111">`Main` doit être [statique](../../language-reference/keywords/static.md) et ne doit pas être [public](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a1-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="bd5a1-112">(Dans l’exemple précédent, il reçoit l’accès par défaut de [Private](../../language-reference/keywords/private.md).) La classe ou le struct englobant ne doit pas obligatoirement être statique.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="bd5a1-113">`Main` peut avoir un type de retour `void`, `int` ou, à partir de C# 7.1, `Task` ou `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="bd5a1-114">Si et seulement si `Main` retourne un `Task` ou `Task<int>`, la déclaration de `Main` peut inclure le modificateur [`async`](../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a1-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="bd5a1-115">Notez que cela exclut spécifiquement une méthode `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="bd5a1-116">La méthode `Main` peut être déclarée avec ou sans paramètre `string[]`, qui contient des arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="bd5a1-117">Lorsque vous utilisez Visual Studio pour créer des applications Windows, vous pouvez ajouter le paramètre manuellement ou utiliser la méthode <xref:System.Environment.GetCommandLineArgs> pour obtenir les [arguments de ligne de commande](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a1-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="bd5a1-118">Les paramètres sont lus comme des arguments de ligne de commande avec index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="bd5a1-119">Contrairement à C C++et, le nom du programme n’est pas traité comme le premier argument de ligne de commande dans le tableau `args`, mais il s’agit du premier élément de la méthode <xref:System.Environment.GetCommandLineArgs>.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="bd5a1-120">L’ajout des types de retour `async` et `Task`, `Task<int>` simplifie le code de programme lorsque les applications de console doivent démarrer et `await` des opérations asynchrones dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="bd5a1-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bd5a1-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bd5a1-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bd5a1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd5a1-122">See also</span></span>

- [<span data-ttu-id="bd5a1-123">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="bd5a1-123">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="bd5a1-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bd5a1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bd5a1-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bd5a1-125">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="bd5a1-126">À l’intérieur d’un programme C#</span><span class="sxs-lookup"><span data-stu-id="bd5a1-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
