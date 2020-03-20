---
title: IMetaDataImport::EnumPermissionSets, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175445"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="46231-102">IMetaDataImport::EnumPermissionSets, méthode</span><span class="sxs-lookup"><span data-stu-id="46231-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="46231-103">Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="46231-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46231-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46231-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46231-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46231-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="46231-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="46231-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="46231-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="46231-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="46231-108">[dans] Un jeton de métadonnées qui limite la portée de la recherche, ou NULL pour rechercher la portée la plus large possible.</span><span class="sxs-lookup"><span data-stu-id="46231-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="46231-109">[dans] Drapeaux représentant <xref:System.Security.Permissions.SecurityAction> les valeurs `rPermission`à inclure dans , ou zéro pour retourner toutes les actions.</span><span class="sxs-lookup"><span data-stu-id="46231-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="46231-110">[out] Le tableau utilisé pour stocker les jetons d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="46231-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="46231-111">[in] Taille maximale du tableau `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="46231-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="46231-112">[out] Le nombre de jetons `rPermission`d’autorisation retournés dans .</span><span class="sxs-lookup"><span data-stu-id="46231-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46231-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="46231-113">Return Value</span></span>  
  
|<span data-ttu-id="46231-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46231-114">HRESULT</span></span>|<span data-ttu-id="46231-115">Description</span><span class="sxs-lookup"><span data-stu-id="46231-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="46231-116">`EnumPermissionSets`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="46231-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="46231-117">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="46231-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="46231-118">Dans ce `pcTokens` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="46231-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46231-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46231-119">Requirements</span></span>  
 <span data-ttu-id="46231-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46231-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46231-121">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="46231-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46231-122">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46231-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46231-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46231-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46231-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46231-124">See also</span></span>

- [<span data-ttu-id="46231-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="46231-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="46231-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="46231-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
