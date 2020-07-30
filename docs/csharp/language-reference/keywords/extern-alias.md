---
title: extern alias - Référence C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 891e56b064f8a327abe28293223a85b9d95e8fd3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301812"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="f6d89-102">extern alias (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f6d89-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="f6d89-103">Il se peut que vous deviez référencer deux versions d’assemblys qui ont le même nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="f6d89-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="f6d89-104">Par exemple, vous pourriez avoir à utiliser plusieurs versions d’un assembly dans la même application.</span><span class="sxs-lookup"><span data-stu-id="f6d89-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="f6d89-105">En utilisant un alias d’assembly externe, vous pouvez encapsuler les espaces de noms de chaque assembly dans des espaces de noms racines nommés par l’alias, ce qui permet de les utiliser dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="f6d89-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6d89-106">Le mot clé [extern](./extern.md) est également utilisé comme modificateur de méthode, déclarant une méthode écrite en code non managé.</span><span class="sxs-lookup"><span data-stu-id="f6d89-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="f6d89-107">Pour référencer deux assemblys portant le même nom de type qualifié complet, vous devez spécifier un alias à l’invite de commandes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f6d89-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="f6d89-108">Cela crée les alias externes `GridV1` et `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="f6d89-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="f6d89-109">Pour utiliser ces alias à partir d’un programme, référencez-les en utilisant le mot clé `extern`.</span><span class="sxs-lookup"><span data-stu-id="f6d89-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="f6d89-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f6d89-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="f6d89-111">Chaque déclaration d’alias externe introduit un espace de noms racine supplémentaire qui est parallèle à l’espace de noms global (mais n’est pas compris dedans).</span><span class="sxs-lookup"><span data-stu-id="f6d89-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="f6d89-112">Ainsi, vous pouvez référencer les types de chaque assembly sans ambiguïté en utilisant leur nom qualifié complet, enraciné dans l’alias d’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="f6d89-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="f6d89-113">Dans l’exemple précédent, `GridV1::Grid` serait le contrôle de grille de `grid.dll`, et `GridV2::Grid` serait le contrôle de grille de `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="f6d89-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="f6d89-114">Utilisation de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6d89-114">Using Visual Studio</span></span>

<span data-ttu-id="f6d89-115">Si vous utilisez Visual Studio, les alias peuvent être fournis de la même façon.</span><span class="sxs-lookup"><span data-stu-id="f6d89-115">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="f6d89-116">Ajoutez une référence de *grid.dll* et *grid20.dll* à votre projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6d89-116">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="f6d89-117">Ouvrez un onglet de propriété et modifiez les alias de global en GridV1 et GridV2, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f6d89-117">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="f6d89-118">Utilisez ces alias de la même façon que ci-dessus</span><span class="sxs-lookup"><span data-stu-id="f6d89-118">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="f6d89-119">Vous pouvez maintenant créer un alias pour un espace de noms ou un type à *l’aide de la directive d’alias*.</span><span class="sxs-lookup"><span data-stu-id="f6d89-119">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="f6d89-120">Pour plus d’informations, consultez [using, directive](using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="f6d89-120">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="f6d89-121">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f6d89-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6d89-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6d89-122">See also</span></span>

- [<span data-ttu-id="f6d89-123">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f6d89-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6d89-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f6d89-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f6d89-125">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="f6d89-125">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f6d89-126">::, Opérateur</span><span class="sxs-lookup"><span data-stu-id="f6d89-126">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="f6d89-127">-Reference (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f6d89-127">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
