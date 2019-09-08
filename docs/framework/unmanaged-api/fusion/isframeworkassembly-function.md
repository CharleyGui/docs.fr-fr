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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796317"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="79964-102">IsFrameworkAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="79964-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="79964-103">Obtient une valeur qui indique si l’assembly spécifié est managé.</span><span class="sxs-lookup"><span data-stu-id="79964-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79964-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79964-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="79964-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79964-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="79964-106">dans Nom de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="79964-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="79964-107">à Valeur booléenne qui indique si l’assembly est managé.</span><span class="sxs-lookup"><span data-stu-id="79964-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="79964-108">dans Chaîne non canonique qui contient l’identité unique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="79964-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="79964-109">[in] Taille de `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="79964-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79964-110">Notes</span><span class="sxs-lookup"><span data-stu-id="79964-110">Remarks</span></span>  
 <span data-ttu-id="79964-111">Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="79964-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="79964-112">Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une `true`valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="79964-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="79964-113">Si l’assembly nommé ne fait pas partie de la .NET Framework, ou `pwzAssemblyReference` si le paramètre ne nomme pas d' `pbIsFrameworkAssembly` assembly, `false`contient une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="79964-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79964-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79964-114">Requirements</span></span>  
 <span data-ttu-id="79964-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79964-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79964-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79964-116">See also</span></span>

- [<span data-ttu-id="79964-117">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="79964-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
