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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63c1cb3c417e8e521c6ac8417d260ccb937863f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796743"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="18673-102">IAssemblyCache::UninstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="18673-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="18673-103">Désinstalle l’assembly spécifié du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="18673-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18673-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18673-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18673-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="18673-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="18673-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="18673-107">dans Nom de l’assembly à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="18673-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="18673-108">dans Structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) qui contient les données d’installation de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="18673-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="18673-109">[out, optional] L’une des valeurs de disposition définies dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="18673-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="18673-110">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18673-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="18673-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="18673-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="18673-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="18673-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="18673-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="18673-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="18673-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="18673-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="18673-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="18673-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="18673-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="18673-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18673-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18673-117">Requirements</span></span>  
 <span data-ttu-id="18673-118">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18673-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18673-119">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="18673-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="18673-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18673-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18673-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18673-121">See also</span></span>

- [<span data-ttu-id="18673-122">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="18673-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
