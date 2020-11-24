---
title: CreateAssemblyCache, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 3197c650b4f167e7a5043270797d2c4a62413d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683197"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="e6b8f-102">CreateAssemblyCache, fonction</span><span class="sxs-lookup"><span data-stu-id="e6b8f-102">CreateAssemblyCache Function</span></span>

<span data-ttu-id="e6b8f-103">Obtient un pointeur vers une nouvelle instance [IAssemblyCache](iassemblycache-interface.md) qui représente le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="e6b8f-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6b8f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6b8f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6b8f-105">Parameters</span></span>  

 `ppAsmCache`  
 <span data-ttu-id="e6b8f-106">à Pointeur retourné `IAssemblyCache` .</span><span class="sxs-lookup"><span data-stu-id="e6b8f-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="e6b8f-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="e6b8f-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e6b8f-108">`dwReserved` doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="e6b8f-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b8f-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e6b8f-109">Requirements</span></span>  

 <span data-ttu-id="e6b8f-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b8f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b8f-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e6b8f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e6b8f-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6b8f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6b8f-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b8f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b8f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6b8f-114">See also</span></span>

- [<span data-ttu-id="e6b8f-115">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="e6b8f-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="e6b8f-116">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="e6b8f-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="e6b8f-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e6b8f-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
