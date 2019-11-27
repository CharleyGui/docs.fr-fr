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
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437448"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="36477-102">IMetaDataImport::GetMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="36477-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="36477-103">Obtient des indicateurs qui indiquent la relation entre la méthode référencée par le jeton MethodDef spécifié et la propriété et l’événement associés référencés par le jeton EventProp spécifié.</span><span class="sxs-lookup"><span data-stu-id="36477-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36477-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36477-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36477-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36477-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="36477-106">dans Jeton MethodDef représentant la méthode pour laquelle obtenir les informations de rôle sémantique.</span><span class="sxs-lookup"><span data-stu-id="36477-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="36477-107">dans Jeton représentant la propriété et l’événement associés pour lesquels obtenir le rôle de la méthode.</span><span class="sxs-lookup"><span data-stu-id="36477-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="36477-108">à Pointeur vers les indicateurs de sémantique associés.</span><span class="sxs-lookup"><span data-stu-id="36477-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="36477-109">Cette valeur est un masque de masque de l’énumération [CorMethodSemanticsAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="36477-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36477-110">Notes</span><span class="sxs-lookup"><span data-stu-id="36477-110">Remarks</span></span>  
 <span data-ttu-id="36477-111">La méthode [IMetaDataEmit ::D efineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) définit les indicateurs de sémantique d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="36477-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36477-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36477-112">Requirements</span></span>  
 <span data-ttu-id="36477-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36477-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36477-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="36477-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36477-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="36477-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36477-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36477-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36477-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36477-117">See also</span></span>

- [<span data-ttu-id="36477-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="36477-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="36477-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="36477-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
