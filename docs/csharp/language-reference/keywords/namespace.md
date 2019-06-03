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
ms.openlocfilehash: df921ecc670bf12411dc8b0d828d6c19bb0a1aec
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422746"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="58e50-102">namespace (référence C#)</span><span class="sxs-lookup"><span data-stu-id="58e50-102">namespace (C# Reference)</span></span>

<span data-ttu-id="58e50-103">Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="58e50-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="58e50-104">Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.</span><span class="sxs-lookup"><span data-stu-id="58e50-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="58e50-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="58e50-105">Remarks</span></span>

<span data-ttu-id="58e50-106">Dans un espace de noms, vous pouvez déclarer zéro ou plusieurs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="58e50-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="58e50-107">autre espace de noms</span><span class="sxs-lookup"><span data-stu-id="58e50-107">another namespace</span></span>

- [<span data-ttu-id="58e50-108">class</span><span class="sxs-lookup"><span data-stu-id="58e50-108">class</span></span>](class.md)

- [<span data-ttu-id="58e50-109">interface</span><span class="sxs-lookup"><span data-stu-id="58e50-109">interface</span></span>](interface.md)

- [<span data-ttu-id="58e50-110">struct</span><span class="sxs-lookup"><span data-stu-id="58e50-110">struct</span></span>](struct.md)

- [<span data-ttu-id="58e50-111">enum</span><span class="sxs-lookup"><span data-stu-id="58e50-111">enum</span></span>](enum.md)

- [<span data-ttu-id="58e50-112">delegate</span><span class="sxs-lookup"><span data-stu-id="58e50-112">delegate</span></span>](delegate.md)

<span data-ttu-id="58e50-113">Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="58e50-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="58e50-114">Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="58e50-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="58e50-115">Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="58e50-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="58e50-116">Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="58e50-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="58e50-117">Consultez [Modificateurs d’accès](access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="58e50-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="58e50-118">Il est possible de définir un espace de noms dans deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="58e50-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="58e50-119">Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="58e50-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="58e50-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="58e50-120">Example</span></span>

<span data-ttu-id="58e50-121">L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="58e50-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="58e50-122">Ressources connexes</span><span class="sxs-lookup"><span data-stu-id="58e50-122">Related resources</span></span>

<span data-ttu-id="58e50-123">Pour plus d’informations sur l’utilisation des espaces de noms, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="58e50-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="58e50-124">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="58e50-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="58e50-125">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="58e50-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="58e50-126">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="58e50-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="58e50-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="58e50-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="58e50-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58e50-128">See also</span></span>

- [<span data-ttu-id="58e50-129">Référence C#</span><span class="sxs-lookup"><span data-stu-id="58e50-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="58e50-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="58e50-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58e50-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="58e50-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="58e50-132">using</span><span class="sxs-lookup"><span data-stu-id="58e50-132">using</span></span>](using-directive.md)
- [<span data-ttu-id="58e50-133">using static</span><span class="sxs-lookup"><span data-stu-id="58e50-133">using static</span></span>](using-static.md)
