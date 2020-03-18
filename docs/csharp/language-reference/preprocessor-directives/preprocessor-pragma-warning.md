---
title: '##pragma warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712466"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="52e4a-102">#pragma warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="52e4a-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="52e4a-103">`#pragma warning` peut activer ou désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="52e4a-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52e4a-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="52e4a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52e4a-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="52e4a-106">Liste de numéros d’avertissement séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="52e4a-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="52e4a-107">Le préfixe « CS » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="52e4a-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="52e4a-108">Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="52e4a-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52e4a-109">Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="52e4a-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52e4a-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="52e4a-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52e4a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52e4a-111">See also</span></span>

- [<span data-ttu-id="52e4a-112">Référence C</span><span class="sxs-lookup"><span data-stu-id="52e4a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="52e4a-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="52e4a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="52e4a-114">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="52e4a-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="52e4a-115">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="52e4a-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
