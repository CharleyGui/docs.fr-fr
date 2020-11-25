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
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728561"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="4a7a1-102">IsFrameworkAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="4a7a1-102">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="4a7a1-103">Obtient une valeur qui indique si l’assembly spécifié est managé.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a7a1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a7a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a7a1-105">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="4a7a1-106">dans Nom de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="4a7a1-107">à Valeur booléenne qui indique si l’assembly est managé.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="4a7a1-108">dans Chaîne non canonique qui contient l’identité unique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="4a7a1-109">[in] Taille de `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a7a1-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a7a1-110">Remarks</span></span>  

 <span data-ttu-id="4a7a1-111">Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="4a7a1-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="4a7a1-112">Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une valeur booléenne `true` .</span><span class="sxs-lookup"><span data-stu-id="4a7a1-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="4a7a1-113">Si l’assembly nommé ne fait pas partie de la .NET Framework, ou si le `pwzAssemblyReference` paramètre ne nomme pas d’assembly, `pbIsFrameworkAssembly` contient une valeur booléenne `false` .</span><span class="sxs-lookup"><span data-stu-id="4a7a1-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a7a1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a7a1-114">Requirements</span></span>  

 <span data-ttu-id="4a7a1-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a7a1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7a1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a7a1-116">See also</span></span>

- [<span data-ttu-id="4a7a1-117">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="4a7a1-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
