---
title: IMetaDataConverter::GetTypeLibFromMetaData, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177628"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="6afd2-102">IMetaDataConverter::GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="6afd2-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="6afd2-103">Obtient un pointeur à une `ITypeLib` instance qui représente la bibliothèque de type qui a les noms spécifiés de bibliothèque et de module.</span><span class="sxs-lookup"><span data-stu-id="6afd2-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6afd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6afd2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6afd2-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="6afd2-106">[dans] Le nom du module de la bibliothèque de type.</span><span class="sxs-lookup"><span data-stu-id="6afd2-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="6afd2-107">[dans] Le nom de la bibliothèque de type.</span><span class="sxs-lookup"><span data-stu-id="6afd2-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="6afd2-108">[out] Un pointeur à un endroit `ITypeLib` qui reçoit l’adresse de l’instance qui représente la bibliothèque de type.</span><span class="sxs-lookup"><span data-stu-id="6afd2-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6afd2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6afd2-109">Requirements</span></span>  
 <span data-ttu-id="6afd2-110">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afd2-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afd2-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="6afd2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6afd2-112">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6afd2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6afd2-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afd2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6afd2-114">See also</span></span>

- [<span data-ttu-id="6afd2-115">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="6afd2-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
