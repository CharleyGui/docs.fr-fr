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
ms.openlocfilehash: 4432b17e5d9aa875d8346b3329cd618e15222040
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771023"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="5bddc-102">IAssemblyCache::CreateAssemblyCacheItem, méthode</span><span class="sxs-lookup"><span data-stu-id="5bddc-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="5bddc-103">Obtient une référence à un nouveau [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="5bddc-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bddc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bddc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bddc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5bddc-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="5bddc-106">[in] Indicateurs définis dans Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="5bddc-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="5bddc-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="5bddc-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5bddc-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="5bddc-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="5bddc-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="5bddc-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5bddc-110">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="5bddc-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5bddc-111">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="5bddc-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="5bddc-112">[out] Retourné `IAssemblyCacheItem` pointeur.</span><span class="sxs-lookup"><span data-stu-id="5bddc-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="5bddc-113">[in, optional] Rendu non canonique, séparés par des virgules `name=value` paires.</span><span class="sxs-lookup"><span data-stu-id="5bddc-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bddc-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5bddc-114">Requirements</span></span>  
 <span data-ttu-id="5bddc-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bddc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bddc-116">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5bddc-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5bddc-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bddc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bddc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bddc-118">See also</span></span>

- [<span data-ttu-id="5bddc-119">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="5bddc-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="5bddc-120">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="5bddc-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
