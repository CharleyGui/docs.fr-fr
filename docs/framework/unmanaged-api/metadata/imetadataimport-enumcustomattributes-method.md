---
title: IMetaDataImport::EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175523"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="7f826-102">IMetaDataImport::EnumCustomAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="7f826-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="7f826-103">Énumère les jetons personnalisés d’attribut-définition associés au type ou au membre spécifié.</span><span class="sxs-lookup"><span data-stu-id="7f826-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f826-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f826-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f826-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f826-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7f826-106">[dans, dehors] Un pointeur à l’enumérateur retourné.</span><span class="sxs-lookup"><span data-stu-id="7f826-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="7f826-107">[dans] Un jeton pour la portée de l’énumération, ou zéro pour tous les attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7f826-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="7f826-108">[dans] Un jeton pour le constructeur du type d’attributs à `null` énumérer, ou pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="7f826-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="7f826-109">[out] Une gamme de jetons d’attribut personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7f826-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7f826-110">[in] Taille maximale du tableau `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="7f826-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="7f826-111">[out, facultatif] Le nombre réel de valeurs `rCustomAttributes`symboliques est retournée dans .</span><span class="sxs-lookup"><span data-stu-id="7f826-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f826-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7f826-112">Return Value</span></span>  
  
|<span data-ttu-id="7f826-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f826-113">HRESULT</span></span>|<span data-ttu-id="7f826-114">Description</span><span class="sxs-lookup"><span data-stu-id="7f826-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7f826-115">`EnumCustomAttributes`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7f826-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7f826-116">Il n’y a pas d’attributs personnalisés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="7f826-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="7f826-117">Dans ce `pcCustomAttributes` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="7f826-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f826-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f826-118">Requirements</span></span>  
 <span data-ttu-id="7f826-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f826-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f826-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7f826-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f826-121">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f826-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f826-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f826-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f826-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f826-123">See also</span></span>

- [<span data-ttu-id="7f826-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="7f826-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7f826-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="7f826-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
