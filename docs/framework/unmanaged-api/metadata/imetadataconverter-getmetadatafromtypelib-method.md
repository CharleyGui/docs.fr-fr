---
title: IMetaDataConverter::GetMetaDataFromTypeLib, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 09a1605deda5b51be604c3b8f0c69fa5adcf9dc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175952"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="73dae-102">IMetaDataConverter::GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="73dae-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="73dae-103">Obtient un pointeur d’interface à une instance [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la `ITypeLib` signature des métadonnées de la bibliothèque de type représentée par l’instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73dae-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73dae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73dae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73dae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73dae-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="73dae-106">[dans] Pointeur `ITypeLib` vers un objet qui représente la bibliothèque de type.</span><span class="sxs-lookup"><span data-stu-id="73dae-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="73dae-107">[out] Pointeur vers un endroit qui `IMetaDataImport` reçoit l’adresse de l’instance qui représente la signature des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="73dae-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73dae-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73dae-108">Requirements</span></span>  
 <span data-ttu-id="73dae-109">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73dae-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73dae-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="73dae-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73dae-111">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73dae-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73dae-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73dae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73dae-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73dae-113">See also</span></span>

- [<span data-ttu-id="73dae-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="73dae-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="73dae-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="73dae-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
