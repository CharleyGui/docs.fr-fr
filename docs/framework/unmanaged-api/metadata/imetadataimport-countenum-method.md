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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f657957d42cef1421ab3aa19f297bd04b0cacd8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781331"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="0e03f-102">IMetaDataImport::CountEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="0e03f-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="0e03f-103">Obtient le nombre d’éléments dans l’énumération qui a été récupérée par l’énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e03f-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e03f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e03f-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e03f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e03f-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0e03f-106">[in] Le handle pour l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0e03f-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="0e03f-107">[out] Le nombre d’éléments énumérés.</span><span class="sxs-lookup"><span data-stu-id="0e03f-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e03f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0e03f-108">Remarks</span></span>  
 <span data-ttu-id="0e03f-109">Le handle spécifié par `hEnum` est obtenue à partir d’une précédente `Enum` *nom* appeler (par exemple, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="0e03f-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e03f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e03f-110">Requirements</span></span>  
 <span data-ttu-id="0e03f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e03f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e03f-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e03f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e03f-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e03f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e03f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e03f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e03f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e03f-115">See also</span></span>

- [<span data-ttu-id="0e03f-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0e03f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0e03f-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0e03f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
