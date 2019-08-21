---
title: namespace, mot clé - Référence C#
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 8cc1d1461a33ab94f8ae399d6ff40f26eaf7f74a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039451"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="38785-102">namespace (référence C#)</span><span class="sxs-lookup"><span data-stu-id="38785-102">namespace (C# Reference)</span></span>

<span data-ttu-id="38785-103">Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="38785-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="38785-104">Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.</span><span class="sxs-lookup"><span data-stu-id="38785-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="38785-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="38785-105">Remarks</span></span>

<span data-ttu-id="38785-106">Dans un espace de noms, vous pouvez déclarer zéro ou plusieurs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="38785-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="38785-107">autre espace de noms</span><span class="sxs-lookup"><span data-stu-id="38785-107">another namespace</span></span>

- [<span data-ttu-id="38785-108">class</span><span class="sxs-lookup"><span data-stu-id="38785-108">class</span></span>](class.md)

- [<span data-ttu-id="38785-109">interface</span><span class="sxs-lookup"><span data-stu-id="38785-109">interface</span></span>](interface.md)

- [<span data-ttu-id="38785-110">struct</span><span class="sxs-lookup"><span data-stu-id="38785-110">struct</span></span>](struct.md)

- [<span data-ttu-id="38785-111">enum</span><span class="sxs-lookup"><span data-stu-id="38785-111">enum</span></span>](enum.md)

- [<span data-ttu-id="38785-112">delegate</span><span class="sxs-lookup"><span data-stu-id="38785-112">delegate</span></span>](delegate.md)

<span data-ttu-id="38785-113">Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="38785-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="38785-114">Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="38785-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="38785-115">Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="38785-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="38785-116">Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="38785-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="38785-117">Consultez [Modificateurs d’accès](access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="38785-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="38785-118">Il est possible de définir un espace de noms dans deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="38785-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="38785-119">Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="38785-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="38785-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="38785-120">Example</span></span>

<span data-ttu-id="38785-121">L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="38785-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="38785-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="38785-122">C# language specification</span></span>

<span data-ttu-id="38785-123">Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="38785-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38785-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38785-124">See also</span></span>

- [<span data-ttu-id="38785-125">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="38785-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="38785-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="38785-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="38785-127">using</span><span class="sxs-lookup"><span data-stu-id="38785-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="38785-128">using static</span><span class="sxs-lookup"><span data-stu-id="38785-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="38785-129">Qualificateur d’alias d’espace de noms`::`</span><span class="sxs-lookup"><span data-stu-id="38785-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="38785-130">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="38785-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
