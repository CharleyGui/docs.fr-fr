---
title: IMetaDataImport::GetMethodSemantics, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65bc4bc74e06368e6c7be9b742a8f311ecadc7fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782318"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="31f8e-102">IMetaDataImport::GetMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="31f8e-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="31f8e-103">Obtient le jeton d’indicateurs indiquant la relation entre la méthode référencée par le jeton MethodDef spécifié et la paire propriété et l’événement référencé par le EventProp spécifié.</span><span class="sxs-lookup"><span data-stu-id="31f8e-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31f8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31f8e-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="31f8e-106">[in] Jeton MethodDef représentant la méthode à obtenir les informations de rôle sémantique.</span><span class="sxs-lookup"><span data-stu-id="31f8e-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="31f8e-107">[in] Jeton représentant l’événement pour lequel obtenir le rôle de la méthode et la paire propriété.</span><span class="sxs-lookup"><span data-stu-id="31f8e-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="31f8e-108">[out] Pointeur vers les indicateurs de sémantique associés.</span><span class="sxs-lookup"><span data-stu-id="31f8e-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="31f8e-109">Cette valeur est un masque de bits à partir de la [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="31f8e-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31f8e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="31f8e-110">Remarks</span></span>  
 <span data-ttu-id="31f8e-111">Le [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) méthode définit les indicateurs de sémantique d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="31f8e-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f8e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31f8e-112">Requirements</span></span>  
 <span data-ttu-id="31f8e-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f8e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f8e-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31f8e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31f8e-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31f8e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31f8e-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f8e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f8e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31f8e-117">See also</span></span>

- [<span data-ttu-id="31f8e-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="31f8e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="31f8e-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="31f8e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
