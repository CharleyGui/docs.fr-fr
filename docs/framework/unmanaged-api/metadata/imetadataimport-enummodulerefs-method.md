---
title: IMetaDataImport::EnumModuleRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afa2d35a193a11360b52bcbdc1d9e5dae16d1c90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782123"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="6df72-102">IMetaDataImport::EnumModuleRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="6df72-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="6df72-103">Énumère les jetons ModuleRef qui représentent des modules importés.</span><span class="sxs-lookup"><span data-stu-id="6df72-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6df72-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df72-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6df72-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6df72-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="6df72-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6df72-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="6df72-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="6df72-108">[out] Tableau utilisé pour stocker les jetons ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="6df72-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6df72-109">[in] Taille maximale du tableau `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="6df72-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="6df72-110">[out] Le nombre de jetons ModuleRef retournés dans `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="6df72-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6df72-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6df72-111">Return Value</span></span>  
  
|<span data-ttu-id="6df72-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6df72-112">HRESULT</span></span>|<span data-ttu-id="6df72-113">Description</span><span class="sxs-lookup"><span data-stu-id="6df72-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6df72-114">`EnumModuleRefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6df72-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6df72-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="6df72-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6df72-116">Dans ce cas, `pcModuleRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="6df72-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6df72-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6df72-117">Requirements</span></span>  
 <span data-ttu-id="6df72-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df72-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df72-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6df72-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6df72-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6df72-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6df72-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df72-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df72-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6df72-122">See also</span></span>

- [<span data-ttu-id="6df72-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6df72-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6df72-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6df72-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
