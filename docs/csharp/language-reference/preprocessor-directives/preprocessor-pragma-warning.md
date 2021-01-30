---
description: '##pragma warning - Référence C#'
title: '##pragma warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215990"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="3763f-103">#pragma warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3763f-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="3763f-104">`#pragma warning` peut activer ou désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="3763f-104">`#pragma warning` can enable or disable certain warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="3763f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3763f-105">Syntax</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a><span data-ttu-id="3763f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3763f-106">Parameters</span></span>

 <span data-ttu-id="3763f-107">`warning-list` Liste de numéros d’avertissement séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="3763f-107">`warning-list` A comma-separated list of warning numbers.</span></span> <span data-ttu-id="3763f-108">Le préfixe « CS » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="3763f-108">The "CS" prefix is optional.</span></span>

 <span data-ttu-id="3763f-109">Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="3763f-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="3763f-110">Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="3763f-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

## <a name="example"></a><span data-ttu-id="3763f-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3763f-111">Example</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a><span data-ttu-id="3763f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3763f-112">See also</span></span>

- [<span data-ttu-id="3763f-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3763f-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3763f-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3763f-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3763f-115">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="3763f-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="3763f-116">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="3763f-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
- [<span data-ttu-id="3763f-117">Comment supprimer des avertissements d’analyse du code</span><span class="sxs-lookup"><span data-stu-id="3763f-117">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
