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
ms.openlocfilehash: ef7057ad19fd34750bd15d358e9c1ebb1289cd44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338062"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="ec220-102">IMetaDataImport::EnumInterfaceImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="ec220-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="ec220-103">Énumère toutes les interfaces implémentées par le `TypeDef`spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec220-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="ec220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec220-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec220-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="ec220-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ec220-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="ec220-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ec220-107">dans Jeton du TypeDef dont les jetons MethodDef représentant des implémentations d’interface doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="ec220-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="ec220-108">à Tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="ec220-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ec220-109">dans Longueur maximale du tableau de `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="ec220-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="ec220-110">à Nombre réel de jetons retournés dans `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="ec220-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec220-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ec220-111">Return Value</span></span>  
  
|<span data-ttu-id="ec220-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec220-112">HRESULT</span></span>|<span data-ttu-id="ec220-113">Description</span><span class="sxs-lookup"><span data-stu-id="ec220-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ec220-114">`EnumInterfaceImpls` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ec220-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ec220-115">Il n’y a aucun jeton MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="ec220-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="ec220-116">Dans ce cas, `pcImpls` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="ec220-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ec220-117">Notes</span><span class="sxs-lookup"><span data-stu-id="ec220-117">Remarks</span></span>

<span data-ttu-id="ec220-118">L’énumération retourne une collection de `mdInterfaceImpl` jetons pour chaque interface implémentée par le `TypeDef`spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec220-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="ec220-119">Les jetons d’interface sont retournés dans l’ordre dans lequel les interfaces ont été spécifiées (par `DefineTypeDef` ou `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="ec220-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="ec220-120">Les propriétés des jetons de `mdInterfaceImpl` retournés peuvent être interrogées à l’aide de [GetInterfaceImplProps,](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec220-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ec220-121">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ec220-121">Requirements</span></span>  
 <span data-ttu-id="ec220-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec220-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec220-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec220-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec220-124">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec220-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec220-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec220-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec220-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec220-126">See also</span></span>

- [<span data-ttu-id="ec220-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ec220-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ec220-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ec220-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
