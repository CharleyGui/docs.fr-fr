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
ms.openlocfilehash: a031cdb875b5eb046428d4d235d3093caddb7a6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491288"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="806c0-102">IMetaDataImport::GetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="806c0-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="806c0-103">Obtient un pointeur vers le type natif non managé du champ représenté par le jeton de métadonnées de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="806c0-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="806c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="806c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="806c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="806c0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="806c0-106">dans Jeton de métadonnées qui représente le champ pour lequel obtenir des informations de marshaling d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="806c0-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="806c0-107">à Pointeur vers la signature de métadonnées du type natif du champ.</span><span class="sxs-lookup"><span data-stu-id="806c0-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="806c0-108">à Taille en octets de `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="806c0-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="806c0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="806c0-109">Requirements</span></span>  
 <span data-ttu-id="806c0-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="806c0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="806c0-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="806c0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="806c0-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="806c0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="806c0-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="806c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="806c0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="806c0-114">See also</span></span>

- [<span data-ttu-id="806c0-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="806c0-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="806c0-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="806c0-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
