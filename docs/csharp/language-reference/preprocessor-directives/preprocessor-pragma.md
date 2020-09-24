---
description: '#pragma - Référence C#'
title: '#pragma - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 2788c2589bee149676c5cb2b4212ec7a060a47af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168515"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="97f80-103">#pragma (référence C#)</span><span class="sxs-lookup"><span data-stu-id="97f80-103">#pragma (C# Reference)</span></span>

<span data-ttu-id="97f80-104">La directive `#pragma` fournit au compilateur des instructions spéciales pour la compilation du fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="97f80-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="97f80-105">Les instructions doivent être prises en charge par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="97f80-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="97f80-106">En d’autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="97f80-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="97f80-107">Le compilateur Microsoft C# prend en charge les deux instructions `#pragma` suivantes :</span><span class="sxs-lookup"><span data-stu-id="97f80-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="97f80-108">AVERTISSEMENT #pragma</span><span class="sxs-lookup"><span data-stu-id="97f80-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="97f80-109">somme de contrôle #pragma</span><span class="sxs-lookup"><span data-stu-id="97f80-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="97f80-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97f80-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="97f80-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97f80-111">Parameters</span></span>  

 `pragma-name`  
 <span data-ttu-id="97f80-112">Nom d’une directive pragma reconnue.</span><span class="sxs-lookup"><span data-stu-id="97f80-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="97f80-113">Arguments propres à la directive pragma.</span><span class="sxs-lookup"><span data-stu-id="97f80-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f80-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97f80-114">See also</span></span>

- [<span data-ttu-id="97f80-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="97f80-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97f80-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="97f80-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97f80-117">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="97f80-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="97f80-118">AVERTISSEMENT #pragma</span><span class="sxs-lookup"><span data-stu-id="97f80-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="97f80-119">somme de contrôle #pragma</span><span class="sxs-lookup"><span data-stu-id="97f80-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
