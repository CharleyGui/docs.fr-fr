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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492185"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="2c742-102">IMetaDataImport::EnumInterfaceImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="2c742-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="2c742-103">Énumère toutes les interfaces implémentées par le spécifié `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="2c742-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="2c742-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c742-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c742-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c742-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2c742-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="2c742-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="2c742-107">dans Jeton du TypeDef dont les jetons MethodDef représentant des implémentations d’interface doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="2c742-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="2c742-108">à Tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="2c742-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2c742-109">dans Longueur maximale du `rImpls` tableau.</span><span class="sxs-lookup"><span data-stu-id="2c742-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="2c742-110">à Nombre réel de jetons retournés dans `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="2c742-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c742-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2c742-111">Return Value</span></span>  
  
|<span data-ttu-id="2c742-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c742-112">HRESULT</span></span>|<span data-ttu-id="2c742-113">Description</span><span class="sxs-lookup"><span data-stu-id="2c742-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2c742-114">`EnumInterfaceImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2c742-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2c742-115">Il n’y a aucun jeton MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="2c742-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="2c742-116">Dans ce cas, `pcImpls` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="2c742-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="2c742-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c742-117">Remarks</span></span>

<span data-ttu-id="2c742-118">L’énumération retourne une collection de `mdInterfaceImpl` jetons pour chaque interface implémentée par le spécifié `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="2c742-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="2c742-119">Les jetons d’interface sont retournés dans l’ordre dans lequel les interfaces ont été spécifiées (par le biais de `DefineTypeDef` ou `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="2c742-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="2c742-120">Les propriétés des jetons retournés `mdInterfaceImpl` peuvent être interrogées à l’aide de [GetInterfaceImplProps,](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="2c742-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="2c742-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c742-121">Requirements</span></span>  
 <span data-ttu-id="2c742-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c742-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c742-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c742-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c742-124">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c742-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c742-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c742-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c742-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c742-126">See also</span></span>

- [<span data-ttu-id="2c742-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2c742-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2c742-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2c742-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
