---
title: IMetaDataImport::GetFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40d1817b9eb7f341899efddb469c7fa17a8f8c0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782395"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="2c0b0-102">IMetaDataImport::GetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="2c0b0-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="2c0b0-103">Obtient un pointeur vers le type natif non managé du champ représenté par le jeton de métadonnées de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c0b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c0b0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c0b0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2c0b0-106">[in] Le jeton de métadonnées qui représente le champ pour obtenir des informations de marshaling interop pour.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="2c0b0-107">[out] Pointeur vers la signature de métadonnées du type natif du champ.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="2c0b0-108">[out] La taille en octets de `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c0b0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c0b0-109">Requirements</span></span>  
 <span data-ttu-id="2c0b0-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0b0-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c0b0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c0b0-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c0b0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c0b0-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0b0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c0b0-114">See also</span></span>

- [<span data-ttu-id="2c0b0-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2c0b0-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2c0b0-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2c0b0-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
