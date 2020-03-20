---
title: IMetaDataEmit::DefineSecurityAttributeSet, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: fadd1974cd4fa8a51a06700835f46df24e37d7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175770"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="ca378-102">IMetaDataEmit::DefineSecurityAttributeSet, méthode</span><span class="sxs-lookup"><span data-stu-id="ca378-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="ca378-103">Crée un ensemble d’autorisations de sécurité à attacher à l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca378-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca378-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca378-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca378-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca378-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ca378-106">[dans] Le jeton auquel les informations de sécurité sont jointes.</span><span class="sxs-lookup"><span data-stu-id="ca378-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="ca378-107">[dans] Un éventail `COR_SECATTR` de structures.</span><span class="sxs-lookup"><span data-stu-id="ca378-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="ca378-108">[dans] Le nombre d’éléments dans `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="ca378-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="ca378-109">[out] Si la méthode échoue, spécifie l’index de `rSecAttrs` l’élément qui a causé le problème.</span><span class="sxs-lookup"><span data-stu-id="ca378-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca378-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca378-110">Requirements</span></span>  
 <span data-ttu-id="ca378-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca378-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca378-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ca378-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca378-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca378-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca378-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca378-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca378-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca378-115">See also</span></span>

- [<span data-ttu-id="ca378-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ca378-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ca378-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ca378-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
