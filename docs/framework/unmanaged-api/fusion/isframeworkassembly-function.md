---
title: IsFrameworkAssembly, fonction
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123069"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="56c36-102">IsFrameworkAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="56c36-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="56c36-103">Obtient une valeur qui indique si l’assembly spécifié est managé.</span><span class="sxs-lookup"><span data-stu-id="56c36-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56c36-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="56c36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56c36-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="56c36-106">dans Nom de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="56c36-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="56c36-107">à Valeur booléenne qui indique si l’assembly est managé.</span><span class="sxs-lookup"><span data-stu-id="56c36-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="56c36-108">dans Chaîne non canonique qui contient l’identité unique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="56c36-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="56c36-109">[in] Taille de `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="56c36-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56c36-110">Notes</span><span class="sxs-lookup"><span data-stu-id="56c36-110">Remarks</span></span>  
 <span data-ttu-id="56c36-111">Le paramètre `pwzAssemblyReference` est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="56c36-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="56c36-112">Si cet assembly fait partie de la .NET Framework, le paramètre `pbIsFrameworkAssembly` contient une valeur booléenne de `true`.</span><span class="sxs-lookup"><span data-stu-id="56c36-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="56c36-113">Si l’assembly nommé ne fait pas partie de la .NET Framework, ou si le paramètre `pwzAssemblyReference` ne nomme pas un assembly, `pbIsFrameworkAssembly` contient une valeur booléenne de `false`.</span><span class="sxs-lookup"><span data-stu-id="56c36-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c36-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="56c36-114">Requirements</span></span>  
 <span data-ttu-id="56c36-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56c36-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c36-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56c36-116">See also</span></span>

- [<span data-ttu-id="56c36-117">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="56c36-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
