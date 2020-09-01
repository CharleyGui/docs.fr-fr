---
description: namespace, mot clé - Référence C#
title: namespace, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139578"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="16b76-103">namespace (référence C#)</span><span class="sxs-lookup"><span data-stu-id="16b76-103">namespace (C# Reference)</span></span>

<span data-ttu-id="16b76-104">Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="16b76-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="16b76-105">Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.</span><span class="sxs-lookup"><span data-stu-id="16b76-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="16b76-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="16b76-106">Remarks</span></span>

<span data-ttu-id="16b76-107">Dans un espace de noms, vous pouvez déclarer zéro ou plusieurs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="16b76-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="16b76-108">autre espace de noms</span><span class="sxs-lookup"><span data-stu-id="16b76-108">another namespace</span></span>

- [<span data-ttu-id="16b76-109">class</span><span class="sxs-lookup"><span data-stu-id="16b76-109">class</span></span>](class.md)

- [<span data-ttu-id="16b76-110">interface</span><span class="sxs-lookup"><span data-stu-id="16b76-110">interface</span></span>](interface.md)

- [<span data-ttu-id="16b76-111">modélis</span><span class="sxs-lookup"><span data-stu-id="16b76-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="16b76-112">variables</span><span class="sxs-lookup"><span data-stu-id="16b76-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="16b76-113">delegate</span><span class="sxs-lookup"><span data-stu-id="16b76-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="16b76-114">Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="16b76-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="16b76-115">Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="16b76-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="16b76-116">Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="16b76-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="16b76-117">Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="16b76-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="16b76-118">Consultez [Modificateurs d’accès](access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="16b76-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="16b76-119">Il est possible de définir un espace de noms dans deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="16b76-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="16b76-120">Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="16b76-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="16b76-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="16b76-121">Example</span></span>

<span data-ttu-id="16b76-122">L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="16b76-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="16b76-123">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="16b76-123">C# language specification</span></span>

<span data-ttu-id="16b76-124">Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="16b76-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16b76-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16b76-125">See also</span></span>

- [<span data-ttu-id="16b76-126">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="16b76-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="16b76-127">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="16b76-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="16b76-128">à</span><span class="sxs-lookup"><span data-stu-id="16b76-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="16b76-129">using static</span><span class="sxs-lookup"><span data-stu-id="16b76-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="16b76-130">Qualificateur d’alias d’espace de noms`::`</span><span class="sxs-lookup"><span data-stu-id="16b76-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="16b76-131">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="16b76-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
