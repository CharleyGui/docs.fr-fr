---
title: Types imbriqués - Guide de programmation C#
description: Un type défini dans une classe, un struct ou une interface est appelé un type imbriqué en C#.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864941"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="ded32-103">Types imbriqués (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ded32-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="ded32-104">Un type défini dans une [classe](../../language-reference/keywords/class.md), un [struct](../../language-reference/builtin-types/struct.md)ou une [interface](../../language-reference/keywords/interface.md) est appelé un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="ded32-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="ded32-105">Par exemple</span><span class="sxs-lookup"><span data-stu-id="ded32-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="ded32-106">Que le type externe soit une classe, une interface ou un struct, les types imbriqués sont [privés](../../language-reference/keywords/private.md)par défaut ; ils sont accessibles uniquement à partir de leur type conteneur.</span><span class="sxs-lookup"><span data-stu-id="ded32-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="ded32-107">Dans l’exemple précédent, la classe `Nested` est inaccessible aux types externes.</span><span class="sxs-lookup"><span data-stu-id="ded32-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="ded32-108">Vous pouvez aussi spécifier un [modificateur d’accès](../../language-reference/keywords/access-modifiers.md) pour définir l’accessibilité d’un type imbriqué, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="ded32-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="ded32-109">Les types imbriqués d’une **classe** peuvent être [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) ou [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="ded32-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="ded32-110">Cependant, le fait de définir une classe imbriquée `protected`, `protected internal` ou `private protected` à l’intérieur d’une [classe sealed](../../language-reference/keywords/sealed.md) a pour effet de générer l’avertissement de compilateur [CS0628](../../misc/cs0628.md), « nouveau membre protected déclaré dans une classe sealed ».</span><span class="sxs-lookup"><span data-stu-id="ded32-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="ded32-111">Les types imbriqués d’un **struct** peuvent être [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md) ou [private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="ded32-111">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="ded32-112">L’exemple suivant fait passer le type de la classe `Nested` à public :</span><span class="sxs-lookup"><span data-stu-id="ded32-112">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="ded32-113">Le type imbriqué (ou interne) peut accéder au type conteneur (ou externe).</span><span class="sxs-lookup"><span data-stu-id="ded32-113">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="ded32-114">Pour accéder au type conteneur, passez-le en tant qu’argument au constructeur du type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="ded32-114">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="ded32-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ded32-115">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="ded32-116">Un type imbriqué a accès à tous les membres qui sont accessibles à son type conteneur.</span><span class="sxs-lookup"><span data-stu-id="ded32-116">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="ded32-117">Il peut accéder aux membres privés et protégés du type conteneur, y compris à tous les membres protégés hérités.</span><span class="sxs-lookup"><span data-stu-id="ded32-117">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="ded32-118">Dans la déclaration précédente, le nom complet de classe `Nested` est `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="ded32-118">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="ded32-119">Il s'agit du nom utilisé pour créer une instance de la classe imbriquée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ded32-119">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="ded32-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ded32-120">See also</span></span>

- [<span data-ttu-id="ded32-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ded32-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ded32-122">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="ded32-122">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ded32-123">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="ded32-123">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="ded32-124">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="ded32-124">Constructors</span></span>](./constructors.md)
