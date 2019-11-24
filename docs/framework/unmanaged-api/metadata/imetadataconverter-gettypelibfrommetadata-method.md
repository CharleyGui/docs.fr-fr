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
ms.openlocfilehash: 9da4e34fa948db2fc73cbde813bac9b3430605ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436250"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="fcfa6-102">IMetaDataConverter::GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="fcfa6-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="fcfa6-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span><span class="sxs-lookup"><span data-stu-id="fcfa6-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcfa6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcfa6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcfa6-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="fcfa6-106">[in] The name of the type library's module.</span><span class="sxs-lookup"><span data-stu-id="fcfa6-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="fcfa6-107">[in] The name of the type library.</span><span class="sxs-lookup"><span data-stu-id="fcfa6-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="fcfa6-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span><span class="sxs-lookup"><span data-stu-id="fcfa6-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfa6-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="fcfa6-109">Requirements</span></span>  
 <span data-ttu-id="fcfa6-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfa6-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfa6-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcfa6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcfa6-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcfa6-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcfa6-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfa6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfa6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcfa6-114">See also</span></span>

- [<span data-ttu-id="fcfa6-115">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="fcfa6-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
