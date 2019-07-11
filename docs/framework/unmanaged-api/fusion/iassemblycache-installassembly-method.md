---
title: IAssemblyCache::InstallAssembly, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd420f0f166b0b17e5fbaf08d6bedd6651188b1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778743"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="0c881-102">IAssemblyCache::InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="0c881-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="0c881-103">Installe l’assembly spécifié dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="0c881-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c881-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c881-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c881-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c881-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="0c881-106">[in] Indicateurs définis dans Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="0c881-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="0c881-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="0c881-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="0c881-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="0c881-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="0c881-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="0c881-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="0c881-110">[in] Le chemin d’accès au manifeste de l’assembly à installer.</span><span class="sxs-lookup"><span data-stu-id="0c881-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="0c881-111">[in] Un [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure qui contient les données pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="0c881-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c881-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0c881-112">Requirements</span></span>  
 <span data-ttu-id="0c881-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c881-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c881-114">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0c881-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0c881-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c881-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c881-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c881-116">See also</span></span>

- [<span data-ttu-id="0c881-117">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="0c881-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
