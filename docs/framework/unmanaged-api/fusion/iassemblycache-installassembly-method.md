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
ms.openlocfilehash: 230b904dd1cca1a1289713e3df7a709bd1c3a22b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696893"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="981b9-102">IAssemblyCache::InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="981b9-102">IAssemblyCache::InstallAssembly Method</span></span>

<span data-ttu-id="981b9-103">Installe l’assembly spécifié dans la Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="981b9-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="981b9-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="981b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="981b9-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="981b9-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="981b9-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="981b9-107">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="981b9-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="981b9-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="981b9-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="981b9-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="981b9-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="981b9-110">dans Chemin d’accès au manifeste de l’assembly à installer.</span><span class="sxs-lookup"><span data-stu-id="981b9-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="981b9-111">dans Structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) qui contient des données pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="981b9-111">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="981b9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="981b9-112">Requirements</span></span>  

 <span data-ttu-id="981b9-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="981b9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981b9-114">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="981b9-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="981b9-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981b9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="981b9-116">See also</span></span>

- [<span data-ttu-id="981b9-117">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="981b9-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
