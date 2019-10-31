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
ms.openlocfilehash: 5ef100680328e9ad6261bb9188d7509efa9ab479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108868"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="8ad9c-102">CreateAssemblyCache, fonction</span><span class="sxs-lookup"><span data-stu-id="8ad9c-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="8ad9c-103">Obtient un pointeur vers une nouvelle instance [IAssemblyCache](iassemblycache-interface.md) qui représente le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="8ad9c-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ad9c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad9c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ad9c-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="8ad9c-106">à Pointeur de `IAssemblyCache` retourné.</span><span class="sxs-lookup"><span data-stu-id="8ad9c-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="8ad9c-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="8ad9c-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8ad9c-108">`dwReserved` doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="8ad9c-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad9c-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="8ad9c-109">Requirements</span></span>  
 <span data-ttu-id="8ad9c-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad9c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad9c-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8ad9c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8ad9c-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ad9c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ad9c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad9c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad9c-114">See also</span></span>

- [<span data-ttu-id="8ad9c-115">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="8ad9c-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="8ad9c-116">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="8ad9c-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="8ad9c-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="8ad9c-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
