---
title: IMetaDataEmit::SetPinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175588"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="acf95-102">IMetaDataEmit::SetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="acf95-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="acf95-103">Définit ou modifie les caractéristiques de la signature PInvoke d’une méthode, tel que défini par un appel antérieur à [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="acf95-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acf95-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acf95-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="acf95-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="acf95-106">[dans] L’information `mdToken` cartographique s’applique.</span><span class="sxs-lookup"><span data-stu-id="acf95-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="acf95-107">[dans] Drapeaux utilisés par PInvoke pour faire la cartographie.</span><span class="sxs-lookup"><span data-stu-id="acf95-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="acf95-108">C’est un peu `CorPinvokeMap` de valeur.</span><span class="sxs-lookup"><span data-stu-id="acf95-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="acf95-109">[dans] Le nom de l’exportation cible dans le DLL indigène.</span><span class="sxs-lookup"><span data-stu-id="acf95-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="acf95-110">[dans] Le `mdModuleRef` jeton pour la cible non gestion DLL.</span><span class="sxs-lookup"><span data-stu-id="acf95-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf95-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="acf95-111">Requirements</span></span>  
 <span data-ttu-id="acf95-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acf95-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acf95-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="acf95-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="acf95-114">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="acf95-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acf95-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acf95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf95-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acf95-116">See also</span></span>

- [<span data-ttu-id="acf95-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="acf95-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="acf95-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="acf95-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
