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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008827"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="ca8bd-102">IMetaDataEmit::SetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="ca8bd-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="ca8bd-103">Termine la disposition des champs pour une classe qui a été définie par un appel antérieur à la [méthode DefineTypeDef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="ca8bd-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca8bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca8bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca8bd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca8bd-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ca8bd-106">dans `mdTypeDef`Jeton qui spécifie la classe à mettre en sortie.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="ca8bd-107">dans Taille de compression : 1, 2, 4, 8 ou 16 octets.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="ca8bd-108">La taille de compression est le nombre d’octets entre les champs adjacents.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="ca8bd-109">dans Tableau de structures [COR_FIELD_OFFSET](cor-field-offset-structure.md) , chacune spécifiant un champ de la classe et l’offset du champ dans la classe.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="ca8bd-110">Terminez le tableau avec `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="ca8bd-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="ca8bd-111">dans Taille, en octets, de la classe.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca8bd-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="ca8bd-112">Remarks</span></span>  
 <span data-ttu-id="ca8bd-113">La classe est initialement définie en appelant la méthode [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md) et en spécifiant l’une des trois dispositions pour les champs de la classe : automatique, séquentielle ou explicite.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="ca8bd-114">Normalement, vous utilisez la disposition automatique et laissez le runtime choisir la meilleure façon de disposer les champs.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="ca8bd-115">Toutefois, vous souhaiterez peut-être disposer des champs présentés en fonction de la structure utilisée par le code non managé.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="ca8bd-116">Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :</span><span class="sxs-lookup"><span data-stu-id="ca8bd-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="ca8bd-117">Disposition séquentielle : spécifiez la taille de compression.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="ca8bd-118">Un champ est aligné en fonction de sa taille naturelle ou de sa taille de compression, selon la valeur la plus petite du décalage du champ.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="ca8bd-119">Définissez `rFieldOffsets` et `ulClassSize` sur zéro.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="ca8bd-120">Disposition explicite : spécifiez le décalage de chaque champ ou spécifiez la taille de la classe et la taille de la compression.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca8bd-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca8bd-121">Requirements</span></span>  
 <span data-ttu-id="ca8bd-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca8bd-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca8bd-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ca8bd-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca8bd-124">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca8bd-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca8bd-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca8bd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8bd-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca8bd-126">See also</span></span>

- [<span data-ttu-id="ca8bd-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ca8bd-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ca8bd-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ca8bd-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
