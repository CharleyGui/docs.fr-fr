---
description: '##pragma warning - Référence C#'
title: '##pragma warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168528"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="766cd-103">#pragma warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="766cd-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="766cd-104">`#pragma warning` peut activer ou désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="766cd-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="766cd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="766cd-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="766cd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="766cd-106">Parameters</span></span>  

 `warning-list`  
 <span data-ttu-id="766cd-107">Liste de numéros d’avertissement séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="766cd-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="766cd-108">Le préfixe « CS » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="766cd-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="766cd-109">Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="766cd-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="766cd-110">Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="766cd-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="766cd-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="766cd-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="766cd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="766cd-112">See also</span></span>

- [<span data-ttu-id="766cd-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="766cd-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="766cd-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="766cd-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="766cd-115">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="766cd-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="766cd-116">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="766cd-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
