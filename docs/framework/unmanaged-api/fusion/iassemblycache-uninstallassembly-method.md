---
title: IAssemblyCache::UninstallAssembly, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 539a8edf6d7248235a6e672edc9464679a2eab82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134500"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="b647c-102">IAssemblyCache::UninstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="b647c-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="b647c-103">Uninstalls the specified assembly from the global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="b647c-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b647c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b647c-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b647c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b647c-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b647c-106">[in] Flags defined in Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b647c-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="b647c-107">[in] The name of the assembly to uninstall.</span><span class="sxs-lookup"><span data-stu-id="b647c-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b647c-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span><span class="sxs-lookup"><span data-stu-id="b647c-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="b647c-109">[out, optional] One of the disposition values defined in Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b647c-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="b647c-110">Possible values include the following:</span><span class="sxs-lookup"><span data-stu-id="b647c-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="b647c-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="b647c-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="b647c-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="b647c-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="b647c-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="b647c-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="b647c-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="b647c-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="b647c-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="b647c-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="b647c-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="b647c-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b647c-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="b647c-117">Requirements</span></span>  
 <span data-ttu-id="b647c-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b647c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b647c-119">**Header:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b647c-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b647c-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b647c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b647c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b647c-121">See also</span></span>

- [<span data-ttu-id="b647c-122">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="b647c-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
