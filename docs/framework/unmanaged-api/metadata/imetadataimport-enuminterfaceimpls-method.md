---
title: IMetaDataImport::EnumInterfaceImpls, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175497"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="29115-102">IMetaDataImport::EnumInterfaceImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="29115-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="29115-103">Énumère toutes les interfaces mises `TypeDef`en œuvre par les spécifiés .</span><span class="sxs-lookup"><span data-stu-id="29115-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="29115-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29115-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29115-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29115-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="29115-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="29115-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="29115-107">[dans] Le jeton du TypeDef dont les jetons MethodDef représentant les implémentations d’interface doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="29115-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="29115-108">[out] Le tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="29115-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29115-109">[dans] La longueur maximale `rImpls` du tableau.</span><span class="sxs-lookup"><span data-stu-id="29115-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="29115-110">[out] Le nombre réel de jetons retournés dans `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="29115-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29115-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="29115-111">Return Value</span></span>  
  
|<span data-ttu-id="29115-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29115-112">HRESULT</span></span>|<span data-ttu-id="29115-113">Description</span><span class="sxs-lookup"><span data-stu-id="29115-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29115-114">`EnumInterfaceImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="29115-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29115-115">Il n’y a pas de jetons MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="29115-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="29115-116">Dans ce `pcImpls` cas, est réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="29115-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="29115-117">Notes </span><span class="sxs-lookup"><span data-stu-id="29115-117">Remarks</span></span>

<span data-ttu-id="29115-118">L’énumération renvoie `mdInterfaceImpl` une collection de jetons pour `TypeDef`chaque interface implémentée par le spécifié .</span><span class="sxs-lookup"><span data-stu-id="29115-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="29115-119">Les jetons d’interface sont retournés dans `DefineTypeDef` l’ordre les interfaces ont été spécifiées (par ou). `SetTypeDefProps`</span><span class="sxs-lookup"><span data-stu-id="29115-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="29115-120">Propriétés des `mdInterfaceImpl` jetons retournés peuvent être interrogés à l’aide [de GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="29115-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="29115-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="29115-121">Requirements</span></span>  
 <span data-ttu-id="29115-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29115-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29115-123">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="29115-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29115-124">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29115-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29115-125">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29115-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29115-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29115-126">See also</span></span>

- [<span data-ttu-id="29115-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="29115-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29115-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="29115-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
