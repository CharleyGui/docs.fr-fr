---
title: IMetaDataImport::EnumTypeSpecs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503716"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="a9587-102">IMetaDataImport::EnumTypeSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="a9587-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="a9587-103">Énumère les jetons TypeSpec définis dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="a9587-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9587-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9587-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9587-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9587-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a9587-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a9587-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a9587-107">Cette valeur doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="a9587-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="a9587-108">à Tableau utilisé pour stocker les jetons TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="a9587-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a9587-109">[in] Taille maximale du tableau `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="a9587-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="a9587-110">à Nombre de jetons TypeSpec retournés dans `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="a9587-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9587-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a9587-111">Return Value</span></span>  
  
|<span data-ttu-id="a9587-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9587-112">HRESULT</span></span>|<span data-ttu-id="a9587-113">Description</span><span class="sxs-lookup"><span data-stu-id="a9587-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a9587-114">`EnumTypeSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a9587-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a9587-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a9587-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a9587-116">Dans ce cas, `pcTypeSpecs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="a9587-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9587-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9587-117">Remarks</span></span>  
 <span data-ttu-id="a9587-118">Les jetons TypeSpec sont créés par la méthode [IMetaDataEmit :: GetTokenFromTypeSpec,](imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9587-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9587-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a9587-119">Requirements</span></span>  
 <span data-ttu-id="a9587-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9587-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9587-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a9587-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9587-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9587-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9587-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9587-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9587-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9587-124">See also</span></span>

- [<span data-ttu-id="a9587-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a9587-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a9587-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a9587-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
