---
title: Tableaux implicitement typés - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705715"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="07c89-102">Tableaux implicitement typés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="07c89-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="07c89-103">Vous pouvez créer un tableau implicitement typé dans lequel le type de l’instance de tableau est déduit à partir des éléments spécifiés dans l’initialiseur de tableau.</span><span class="sxs-lookup"><span data-stu-id="07c89-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="07c89-104">Les règles applicables à une variable implicitement typée s’appliquent aussi aux tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="07c89-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="07c89-105">Pour plus d’informations, consultez [Variables locales implicitement typées](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="07c89-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="07c89-106">Les tableaux implicitement typés sont généralement utilisés dans les expressions de requête avec des types anonymes et des initialiseurs d’objets et de collections.</span><span class="sxs-lookup"><span data-stu-id="07c89-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="07c89-107">Les exemples suivants montrent comment créer un tableau implicitement typé :</span><span class="sxs-lookup"><span data-stu-id="07c89-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="07c89-108">Dans l’exemple précédent, vous pouvez constater que dans le cas des tableaux implicitement typés, aucun crochet n’est utilisé à gauche de l’instruction d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="07c89-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="07c89-109">Notez aussi que les tableaux en escalier sont initialisés à l’aide de `new []` à l’instar des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="07c89-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="07c89-110">Tableaux implicitement typés dans les initialiseurs d’objets</span><span class="sxs-lookup"><span data-stu-id="07c89-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="07c89-111">Quand vous créez un type anonyme qui contient un tableau, le tableau doit être implicitement typé dans l’initialiseur d’objet du type.</span><span class="sxs-lookup"><span data-stu-id="07c89-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="07c89-112">Dans l’exemple suivant, `contacts` est un tableau implicitement typé de types anonymes, dont chacun contient un tableau nommé `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="07c89-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="07c89-113">Notez que le mot clé `var` n’est pas utilisé dans les initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="07c89-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="07c89-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07c89-114">See also</span></span>

- [<span data-ttu-id="07c89-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="07c89-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="07c89-116">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="07c89-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="07c89-117">Tableaux</span><span class="sxs-lookup"><span data-stu-id="07c89-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="07c89-118">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="07c89-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="07c89-119">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="07c89-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="07c89-120">var</span><span class="sxs-lookup"><span data-stu-id="07c89-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="07c89-121">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="07c89-121">LINQ in C#</span></span>](../../linq/index.md)
