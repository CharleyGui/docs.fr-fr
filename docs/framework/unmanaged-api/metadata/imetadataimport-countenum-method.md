---
title: IMetaDataImport::CountEnum, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177363"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="5644a-102">IMetaDataImport::CountEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="5644a-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="5644a-103">Obtient le nombre d’éléments dans le recensement qui a été récupéré par l’énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="5644a-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5644a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5644a-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5644a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5644a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5644a-106">[dans] La poignée de l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="5644a-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="5644a-107">[out] Le nombre d’éléments énumérés.</span><span class="sxs-lookup"><span data-stu-id="5644a-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5644a-108">Notes </span><span class="sxs-lookup"><span data-stu-id="5644a-108">Remarks</span></span>  
 <span data-ttu-id="5644a-109">La poignée `hEnum` spécifiée par est `Enum`obtenue à partir d’un précédent appel *nom* (par exemple, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="5644a-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5644a-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5644a-110">Requirements</span></span>  
 <span data-ttu-id="5644a-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5644a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5644a-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="5644a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5644a-113">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5644a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5644a-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5644a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5644a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5644a-115">See also</span></span>

- [<span data-ttu-id="5644a-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="5644a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5644a-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="5644a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
