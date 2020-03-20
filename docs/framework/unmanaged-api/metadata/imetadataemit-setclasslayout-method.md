---
title: IMetaDataEmit::SetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177572"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="08276-102">IMetaDataEmit::SetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="08276-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="08276-103">Termine la disposition des champs pour une classe qui a été définie par un appel préalable à [DefineTypeDef Méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="08276-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08276-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08276-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08276-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08276-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="08276-106">[dans] Un `mdTypeDef` jeton qui spécifie la classe à mettre en place.</span><span class="sxs-lookup"><span data-stu-id="08276-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="08276-107">[dans] La taille d’emballage: 1, 2, 4, 8 ou 16 octets.</span><span class="sxs-lookup"><span data-stu-id="08276-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="08276-108">La taille d’emballage est le nombre d’octets entre les champs adjacents.</span><span class="sxs-lookup"><span data-stu-id="08276-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="08276-109">[dans] Un éventail de structures [COR_FIELD_OFFSET,](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) chacune spécifie un champ de la classe et le décalage du champ au sein de la classe.</span><span class="sxs-lookup"><span data-stu-id="08276-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="08276-110">Terminez le `mdTokenNil`tableau avec .</span><span class="sxs-lookup"><span data-stu-id="08276-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="08276-111">[dans] La taille, dans les octets, de la classe.</span><span class="sxs-lookup"><span data-stu-id="08276-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08276-112">Notes </span><span class="sxs-lookup"><span data-stu-id="08276-112">Remarks</span></span>  
 <span data-ttu-id="08276-113">La classe est initialement définie en appelant la méthode [IMetaDataEmit::DefineTypeDef,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) et en spécifiant l’une des trois mises en page pour les champs de la classe: automatique, séquentielle, ou explicite.</span><span class="sxs-lookup"><span data-stu-id="08276-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="08276-114">Normalement, vous utiliseriez la disposition automatique et laisser le temps d’exécution choisir la meilleure façon d’exposer les champs.</span><span class="sxs-lookup"><span data-stu-id="08276-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="08276-115">Cependant, vous voudrez peut-être que les champs sont énoncés selon l’arrangement que le code non menté utilise.</span><span class="sxs-lookup"><span data-stu-id="08276-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="08276-116">Dans ce cas, choisissez une mise en `SetClassLayout` page séquentielle ou explicite et appelez pour compléter la disposition des champs :</span><span class="sxs-lookup"><span data-stu-id="08276-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="08276-117">Mise en page séquentielle : Spécifier la taille de l’emballage.</span><span class="sxs-lookup"><span data-stu-id="08276-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="08276-118">Un champ est aligné en fonction de sa taille naturelle ou de la taille de l’emballage, selon le plus petit décalage du champ.</span><span class="sxs-lookup"><span data-stu-id="08276-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="08276-119">Définir `rFieldOffsets` `ulClassSize` et à zéro.</span><span class="sxs-lookup"><span data-stu-id="08276-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="08276-120">Mise en page explicite : soit spécifiez le décalage de chaque champ, soit spécifiez la taille de la classe et la taille de l’emballage.</span><span class="sxs-lookup"><span data-stu-id="08276-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08276-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="08276-121">Requirements</span></span>  
 <span data-ttu-id="08276-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08276-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08276-123">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="08276-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08276-124">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08276-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08276-125">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08276-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08276-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08276-126">See also</span></span>

- [<span data-ttu-id="08276-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="08276-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="08276-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="08276-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
