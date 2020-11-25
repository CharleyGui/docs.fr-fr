---
title: IMetaDataImport::EnumMethodSemantics, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720969"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="70f32-102">IMetaDataImport::EnumMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="70f32-102">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="70f32-103">Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.</span><span class="sxs-lookup"><span data-stu-id="70f32-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70f32-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70f32-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="70f32-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="70f32-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="70f32-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="70f32-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="70f32-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="70f32-108">dans Jeton MethodDef qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="70f32-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="70f32-109">à Tableau utilisé pour stocker les événements ou les propriétés.</span><span class="sxs-lookup"><span data-stu-id="70f32-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="70f32-110">[in] Taille maximale du tableau `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="70f32-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="70f32-111">à Nombre d’événements ou de propriétés retournés dans `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="70f32-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70f32-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="70f32-112">Return Value</span></span>  
  
|<span data-ttu-id="70f32-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70f32-113">HRESULT</span></span>|<span data-ttu-id="70f32-114">Description</span><span class="sxs-lookup"><span data-stu-id="70f32-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="70f32-115">`EnumMethodSemantics` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="70f32-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="70f32-116">Il n’y a aucun événement ou propriété à énumérer.</span><span class="sxs-lookup"><span data-stu-id="70f32-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="70f32-117">Dans ce cas, `pcEventProp` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="70f32-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70f32-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="70f32-118">Remarks</span></span>  

 <span data-ttu-id="70f32-119">De nombreux types de common language runtime définissent les événements de *propriété* `Changed` et `On` *Property* `Changed` les méthodes de propriétés associées à leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="70f32-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="70f32-120">Par exemple, le <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type définit une <xref:System.Windows.Forms.Control.Font%2A> propriété, un <xref:System.Windows.Forms.Control.FontChanged> événement et une <xref:System.Windows.Forms.Control.OnFontChanged%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="70f32-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="70f32-121">La méthode d’accesseur Set de la <xref:System.Windows.Forms.Control.Font%2A> propriété appelle la <xref:System.Windows.Forms.Control.OnFontChanged%2A> méthode, qui à son tour déclenche l' <xref:System.Windows.Forms.Control.FontChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="70f32-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="70f32-122">Vous appelez à `EnumMethodSemantics` l’aide du MethodDef pour <xref:System.Windows.Forms.Control.OnFontChanged%2A> pour obtenir des références à la <xref:System.Windows.Forms.Control.Font%2A> propriété et à l' <xref:System.Windows.Forms.Control.FontChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="70f32-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f32-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="70f32-123">Requirements</span></span>  

 <span data-ttu-id="70f32-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70f32-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f32-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="70f32-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70f32-126">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70f32-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70f32-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f32-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f32-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70f32-128">See also</span></span>

- [<span data-ttu-id="70f32-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="70f32-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="70f32-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="70f32-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
