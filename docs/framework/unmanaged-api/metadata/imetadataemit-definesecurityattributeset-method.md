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
ms.openlocfilehash: c33ede841324820da16e33d35bbf5e8f8e75924f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009364"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="ecee9-102">IMetaDataEmit::DefineSecurityAttributeSet, méthode</span><span class="sxs-lookup"><span data-stu-id="ecee9-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="ecee9-103">Crée un jeu d’autorisations de sécurité à attacher à l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="ecee9-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecee9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecee9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecee9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ecee9-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ecee9-106">dans Jeton auquel les informations de sécurité sont jointes.</span><span class="sxs-lookup"><span data-stu-id="ecee9-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="ecee9-107">dans Tableau de `COR_SECATTR` structures.</span><span class="sxs-lookup"><span data-stu-id="ecee9-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="ecee9-108">dans Nombre d’éléments dans `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="ecee9-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="ecee9-109">à Si la méthode échoue, spécifie l’index dans `rSecAttrs` de l’élément qui a provoqué le problème.</span><span class="sxs-lookup"><span data-stu-id="ecee9-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecee9-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ecee9-110">Requirements</span></span>  
 <span data-ttu-id="ecee9-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecee9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecee9-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ecee9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecee9-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecee9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecee9-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecee9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecee9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecee9-115">See also</span></span>

- [<span data-ttu-id="ecee9-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ecee9-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ecee9-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ecee9-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
