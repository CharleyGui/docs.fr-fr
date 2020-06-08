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
ms.openlocfilehash: 79b1493d262288c1d85a56538810e35a73441595
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491755"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="95fe1-102">IMetaDataImport::EnumPermissionSets, méthode</span><span class="sxs-lookup"><span data-stu-id="95fe1-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="95fe1-103">Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="95fe1-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95fe1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="95fe1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95fe1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="95fe1-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="95fe1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="95fe1-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="95fe1-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="95fe1-108">dans Un jeton de métadonnées qui limite l’étendue de la recherche, ou NULL pour effectuer une recherche dans l’étendue la plus étendue possible.</span><span class="sxs-lookup"><span data-stu-id="95fe1-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="95fe1-109">dans Indicateurs représentant les <xref:System.Security.Permissions.SecurityAction> valeurs à inclure dans `rPermission` , ou zéro pour retourner toutes les actions.</span><span class="sxs-lookup"><span data-stu-id="95fe1-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="95fe1-110">à Tableau utilisé pour stocker les jetons d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="95fe1-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="95fe1-111">[in] Taille maximale du tableau `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="95fe1-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="95fe1-112">à Nombre de jetons d’autorisation retournés dans `rPermission` .</span><span class="sxs-lookup"><span data-stu-id="95fe1-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95fe1-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="95fe1-113">Return Value</span></span>  
  
|<span data-ttu-id="95fe1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95fe1-114">HRESULT</span></span>|<span data-ttu-id="95fe1-115">Description</span><span class="sxs-lookup"><span data-stu-id="95fe1-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="95fe1-116">`EnumPermissionSets`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="95fe1-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="95fe1-117">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="95fe1-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="95fe1-118">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="95fe1-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95fe1-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95fe1-119">Requirements</span></span>  
 <span data-ttu-id="95fe1-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95fe1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95fe1-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95fe1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95fe1-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95fe1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95fe1-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95fe1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fe1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95fe1-124">See also</span></span>

- [<span data-ttu-id="95fe1-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="95fe1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="95fe1-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="95fe1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
