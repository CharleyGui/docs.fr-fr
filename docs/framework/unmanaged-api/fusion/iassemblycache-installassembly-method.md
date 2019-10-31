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
ms.openlocfilehash: ec08c786992996ec6f44038ff3c1596cada88484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127081"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="f6415-102">IAssemblyCache::InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="f6415-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="f6415-103">Installe l’assembly spécifié dans la Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f6415-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6415-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6415-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6415-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6415-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="f6415-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="f6415-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="f6415-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="f6415-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="f6415-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="f6415-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="f6415-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="f6415-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="f6415-110">dans Chemin d’accès au manifeste de l’assembly à installer.</span><span class="sxs-lookup"><span data-stu-id="f6415-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="f6415-111">dans Structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) qui contient les données pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="f6415-111">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6415-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="f6415-112">Requirements</span></span>  
 <span data-ttu-id="f6415-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6415-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6415-114">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f6415-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f6415-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6415-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6415-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6415-116">See also</span></span>

- [<span data-ttu-id="f6415-117">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="f6415-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
