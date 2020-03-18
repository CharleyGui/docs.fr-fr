---
title: '#pragma - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712453"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="202fb-102">#pragma (référence C#)</span><span class="sxs-lookup"><span data-stu-id="202fb-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="202fb-103">La directive `#pragma` fournit au compilateur des instructions spéciales pour la compilation du fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="202fb-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="202fb-104">Les instructions doivent être prises en charge par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="202fb-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="202fb-105">En d’autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="202fb-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="202fb-106">Le compilateur Microsoft C# prend en charge les deux instructions `#pragma` suivantes :</span><span class="sxs-lookup"><span data-stu-id="202fb-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="202fb-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="202fb-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="202fb-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="202fb-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="202fb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="202fb-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="202fb-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="202fb-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="202fb-111">Nom d’une directive pragma reconnue.</span><span class="sxs-lookup"><span data-stu-id="202fb-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="202fb-112">Arguments propres à la directive pragma.</span><span class="sxs-lookup"><span data-stu-id="202fb-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202fb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="202fb-113">See also</span></span>

- [<span data-ttu-id="202fb-114">Référence C</span><span class="sxs-lookup"><span data-stu-id="202fb-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="202fb-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="202fb-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="202fb-116">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="202fb-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="202fb-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="202fb-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="202fb-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="202fb-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
