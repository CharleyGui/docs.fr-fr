---
title: IMetaDataImport::IsGlobal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: 8a5dda5861343865a139f6b6b9e2794179b0727a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434719"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="12af9-102">IMetaDataImport::IsGlobal, méthode</span><span class="sxs-lookup"><span data-stu-id="12af9-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="12af9-103">Obtient une valeur qui indique si le champ, la méthode ou le type représenté(e) par le jeton de métadonnées spécifié a une portée globale.</span><span class="sxs-lookup"><span data-stu-id="12af9-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12af9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12af9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12af9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12af9-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="12af9-106">[in] A metadata token that represents a type, field, or method.</span><span class="sxs-lookup"><span data-stu-id="12af9-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="12af9-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="12af9-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12af9-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="12af9-108">Requirements</span></span>  
 <span data-ttu-id="12af9-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12af9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12af9-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12af9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12af9-111">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12af9-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12af9-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12af9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12af9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12af9-113">See also</span></span>

- [<span data-ttu-id="12af9-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="12af9-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="12af9-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="12af9-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
