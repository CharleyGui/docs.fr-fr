---
title: Espaces de noms - Guide de programmation C#
description: En savoir plus sur les espaces de noms en programmation C#. Consultez une vue d’ensemble des propriétés d’espace de noms et affichez des ressources supplémentaires.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: fca2c641520bd9cd19a48bff2119a6f09c3713ea
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382098"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="8fee8-104">Espaces de noms (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8fee8-104">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="8fee8-105">Les espaces de noms sont largement utilisés de deux façons dans la programmation avec C#.</span><span class="sxs-lookup"><span data-stu-id="8fee8-105">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="8fee8-106">Tout d’abord, .NET utilise des espaces de noms pour organiser ses nombreuses classes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="8fee8-106">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="8fee8-107"><xref:System> est un espace de noms et <xref:System.Console> est une classe de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8fee8-107"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="8fee8-108">Vous pouvez utiliser le mot clé `using`. Ainsi, le nom complet n’est pas obligatoire, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8fee8-108">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="8fee8-109">Pour plus d’informations, consultez [Directive using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="8fee8-109">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="8fee8-110">Deuxièmement, la déclaration de vos propres espaces de noms peut vous aider à contrôler l’étendue des noms de classes et de méthodes dans les projets de programmation plus vastes.</span><span class="sxs-lookup"><span data-stu-id="8fee8-110">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="8fee8-111">Utilisez le mot clé [namespace](../../language-reference/keywords/namespace.md) pour déclarer un espace de noms, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8fee8-111">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="8fee8-112">Le nom de l’espace de noms doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide.</span><span class="sxs-lookup"><span data-stu-id="8fee8-112">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="8fee8-113">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8fee8-113">Namespaces overview</span></span>

<span data-ttu-id="8fee8-114">Les espaces de noms ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8fee8-114">Namespaces have the following properties:</span></span>

- <span data-ttu-id="8fee8-115">Ils organisent les projets de code de taille importante.</span><span class="sxs-lookup"><span data-stu-id="8fee8-115">They organize large code projects.</span></span>
- <span data-ttu-id="8fee8-116">Ils sont délimités à l’aide de l’opérateur `.`.</span><span class="sxs-lookup"><span data-stu-id="8fee8-116">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="8fee8-117">La directive `using` évite de devoir spécifier le nom de l’espace de noms pour chaque classe.</span><span class="sxs-lookup"><span data-stu-id="8fee8-117">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="8fee8-118">L’espace de noms `global` est l’espace de noms « racine » : `global::System` fait toujours référence à l’espace de noms <xref:System> .NET.</span><span class="sxs-lookup"><span data-stu-id="8fee8-118">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8fee8-119">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8fee8-119">C# language specification</span></span>

<span data-ttu-id="8fee8-120">Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8fee8-120">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fee8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fee8-121">See also</span></span>

- [<span data-ttu-id="8fee8-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8fee8-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8fee8-123">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8fee8-123">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="8fee8-124">Comment utiliser l’espace de noms My</span><span class="sxs-lookup"><span data-stu-id="8fee8-124">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="8fee8-125">Noms d’identificateurs</span><span class="sxs-lookup"><span data-stu-id="8fee8-125">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="8fee8-126">using, directive</span><span class="sxs-lookup"><span data-stu-id="8fee8-126">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="8fee8-127">::, Opérateur</span><span class="sxs-lookup"><span data-stu-id="8fee8-127">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
