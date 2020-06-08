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
ms.openlocfilehash: 2cfb66203d8f2d69ea188f6913a5ef34dd74791e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503599"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="1d116-102">IMetaDataImport::GetMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="1d116-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="1d116-103">Obtient des indicateurs qui indiquent la relation entre la méthode référencée par le jeton MethodDef spécifié et la propriété et l’événement associés référencés par le jeton EventProp spécifié.</span><span class="sxs-lookup"><span data-stu-id="1d116-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d116-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d116-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d116-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="1d116-106">dans Jeton MethodDef représentant la méthode pour laquelle obtenir les informations de rôle sémantique.</span><span class="sxs-lookup"><span data-stu-id="1d116-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="1d116-107">dans Jeton représentant la propriété et l’événement associés pour lesquels obtenir le rôle de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1d116-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="1d116-108">à Pointeur vers les indicateurs de sémantique associés.</span><span class="sxs-lookup"><span data-stu-id="1d116-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="1d116-109">Cette valeur est un masque de masque de l’énumération [CorMethodSemanticsAttr,](cormethodsemanticsattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1d116-109">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d116-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d116-110">Remarks</span></span>  
 <span data-ttu-id="1d116-111">La méthode [IMetaDataEmit ::D efineproperty](imetadataemit-defineproperty-method.md) définit les indicateurs de sémantique d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1d116-111">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d116-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d116-112">Requirements</span></span>  
 <span data-ttu-id="1d116-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d116-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d116-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1d116-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d116-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1d116-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d116-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d116-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d116-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d116-117">See also</span></span>

- [<span data-ttu-id="1d116-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="1d116-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1d116-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="1d116-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
