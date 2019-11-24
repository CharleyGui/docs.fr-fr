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
ms.openlocfilehash: 0c78ce8192d6456dd1b1be990d87b9209b028e09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440358"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="38a34-102">IMetaDataImport::CountEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="38a34-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="38a34-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span><span class="sxs-lookup"><span data-stu-id="38a34-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38a34-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38a34-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38a34-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="38a34-106">[in] The handle for the enumerator.</span><span class="sxs-lookup"><span data-stu-id="38a34-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="38a34-107">[out] The number of elements enumerated.</span><span class="sxs-lookup"><span data-stu-id="38a34-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38a34-108">Notes</span><span class="sxs-lookup"><span data-stu-id="38a34-108">Remarks</span></span>  
 <span data-ttu-id="38a34-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="38a34-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a34-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="38a34-110">Requirements</span></span>  
 <span data-ttu-id="38a34-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a34-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38a34-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38a34-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38a34-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38a34-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a34-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38a34-115">See also</span></span>

- [<span data-ttu-id="38a34-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="38a34-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="38a34-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="38a34-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
