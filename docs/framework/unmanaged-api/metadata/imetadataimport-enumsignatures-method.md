---
title: IMetaDataImport::EnumSignatures, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 3021124184ab0491337a07144e6f77b5bfea3681
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721970"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="f66a1-102">IMetaDataImport::EnumSignatures, méthode</span><span class="sxs-lookup"><span data-stu-id="f66a1-102">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="f66a1-103">Énumère les jetons Signature représentant des signatures autonomes dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="f66a1-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f66a1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f66a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f66a1-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f66a1-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="f66a1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f66a1-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f66a1-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="f66a1-108">à Tableau utilisé pour stocker les jetons de signature.</span><span class="sxs-lookup"><span data-stu-id="f66a1-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f66a1-109">[in] Taille maximale du tableau `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="f66a1-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="f66a1-110">à Nombre de jetons de signature retournés dans `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="f66a1-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f66a1-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f66a1-111">Return Value</span></span>  
  
|<span data-ttu-id="f66a1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f66a1-112">HRESULT</span></span>|<span data-ttu-id="f66a1-113">Description</span><span class="sxs-lookup"><span data-stu-id="f66a1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f66a1-114">`EnumSignatures` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f66a1-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f66a1-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="f66a1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f66a1-116">Dans ce cas, `pcSignatures` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="f66a1-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f66a1-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="f66a1-117">Remarks</span></span>  

 <span data-ttu-id="f66a1-118">Les jetons de signature sont créés par la méthode [IMetaDataEmit :: GetTokenFromSig,](imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f66a1-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66a1-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f66a1-119">Requirements</span></span>  

 <span data-ttu-id="f66a1-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f66a1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66a1-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f66a1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f66a1-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f66a1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f66a1-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66a1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f66a1-124">See also</span></span>

- [<span data-ttu-id="f66a1-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f66a1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f66a1-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f66a1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
