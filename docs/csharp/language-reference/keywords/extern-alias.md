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
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713549"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="36534-102">extern alias (référence C#)</span><span class="sxs-lookup"><span data-stu-id="36534-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="36534-103">Il se peut que vous deviez référencer deux versions d’assemblys qui ont le même nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="36534-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="36534-104">Par exemple, vous pourriez avoir à utiliser plusieurs versions d’un assembly dans la même application.</span><span class="sxs-lookup"><span data-stu-id="36534-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="36534-105">En utilisant un alias d’assembly externe, vous pouvez encapsuler les espaces de noms de chaque assembly dans des espaces de noms racines nommés par l’alias, ce qui permet de les utiliser dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="36534-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36534-106">Le mot clé [extern](./extern.md) est également utilisé comme modificateur de méthode, déclarant une méthode écrite en code non managé.</span><span class="sxs-lookup"><span data-stu-id="36534-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="36534-107">Pour référencer deux assemblys portant le même nom de type qualifié complet, vous devez spécifier un alias à l’invite de commandes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="36534-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="36534-108">Cela crée les alias externes `GridV1` et `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="36534-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="36534-109">Pour utiliser ces alias à partir d’un programme, référencez-les en utilisant le mot clé `extern`.</span><span class="sxs-lookup"><span data-stu-id="36534-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="36534-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="36534-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="36534-111">Chaque déclaration d’alias externe introduit un espace de noms racine supplémentaire qui est parallèle à l’espace de noms global (mais n’est pas compris dedans).</span><span class="sxs-lookup"><span data-stu-id="36534-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="36534-112">Ainsi, vous pouvez référencer les types de chaque assembly sans ambiguïté en utilisant leur nom qualifié complet, enraciné dans l’alias d’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="36534-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="36534-113">Dans l’exemple précédent, `GridV1::Grid` serait le contrôle de grille de `grid.dll`, et `GridV2::Grid` serait le contrôle de grille de `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="36534-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="36534-114">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="36534-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36534-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36534-115">See also</span></span>

- [<span data-ttu-id="36534-116">Référence C</span><span class="sxs-lookup"><span data-stu-id="36534-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="36534-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="36534-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="36534-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="36534-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="36534-119">:: Opérateur</span><span class="sxs-lookup"><span data-stu-id="36534-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="36534-120">-référence (Options compilateur C)</span><span class="sxs-lookup"><span data-stu-id="36534-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
