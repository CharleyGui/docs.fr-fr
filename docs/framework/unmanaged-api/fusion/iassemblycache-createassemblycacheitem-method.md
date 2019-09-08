---
title: IAssemblyCache::CreateAssemblyCacheItem, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796828"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="5340c-102">IAssemblyCache::CreateAssemblyCacheItem, méthode</span><span class="sxs-lookup"><span data-stu-id="5340c-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="5340c-103">Obtient une référence à un nouvel objet [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5340c-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5340c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5340c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5340c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5340c-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="5340c-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="5340c-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="5340c-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="5340c-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5340c-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="5340c-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="5340c-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="5340c-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5340c-110">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="5340c-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5340c-111">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="5340c-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="5340c-112">à Pointeur retourné `IAssemblyCacheItem` .</span><span class="sxs-lookup"><span data-stu-id="5340c-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="5340c-113">[in, facultatif] Les paires non canoniques, séparées `name=value` par des virgules.</span><span class="sxs-lookup"><span data-stu-id="5340c-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5340c-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5340c-114">Requirements</span></span>  
 <span data-ttu-id="5340c-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5340c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5340c-116">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5340c-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5340c-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5340c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5340c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5340c-118">See also</span></span>

- [<span data-ttu-id="5340c-119">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="5340c-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="5340c-120">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="5340c-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
