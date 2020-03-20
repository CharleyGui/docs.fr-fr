---
title: IMetaDataDispenserEx::GetCORSystemDirectory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175913"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="255b6-102">IMetaDataDispenserEx::GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="255b6-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="255b6-103">Obtient le répertoire qui détient l’heure courante de course de langue commune (CLR).</span><span class="sxs-lookup"><span data-stu-id="255b6-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="255b6-104">Cette méthode n’est prise en charge que pour une utilisation par les débingiers hors-processus.</span><span class="sxs-lookup"><span data-stu-id="255b6-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="255b6-105">S’il est appelé à partir d’un autre composant, il retournera E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="255b6-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255b6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="255b6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="255b6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="255b6-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="255b6-108">[out] Le tampon pour recevoir le nom d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="255b6-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="255b6-109">[dans] La taille, dans les `szBuffer`octets, de .</span><span class="sxs-lookup"><span data-stu-id="255b6-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="255b6-110">[out] Le nombre d’octets `szBuffer`effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="255b6-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="255b6-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="255b6-111">Requirements</span></span>  
 <span data-ttu-id="255b6-112">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="255b6-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255b6-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="255b6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="255b6-114">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="255b6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="255b6-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="255b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="255b6-116">See also</span></span>

- [<span data-ttu-id="255b6-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="255b6-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="255b6-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="255b6-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
