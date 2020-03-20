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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175458"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="668ef-102">IMetaDataImport::EnumMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="668ef-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="668ef-103">Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.</span><span class="sxs-lookup"><span data-stu-id="668ef-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="668ef-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="668ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="668ef-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="668ef-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="668ef-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="668ef-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="668ef-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="668ef-108">[dans] Un jeton MethodDef qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="668ef-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="668ef-109">[out] Le tableau utilisé pour stocker les événements ou les propriétés.</span><span class="sxs-lookup"><span data-stu-id="668ef-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="668ef-110">[in] Taille maximale du tableau `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="668ef-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="668ef-111">[out] Le nombre d’événements `rEventProp`ou de propriétés retournés dans .</span><span class="sxs-lookup"><span data-stu-id="668ef-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="668ef-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="668ef-112">Return Value</span></span>  
  
|<span data-ttu-id="668ef-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="668ef-113">HRESULT</span></span>|<span data-ttu-id="668ef-114">Description</span><span class="sxs-lookup"><span data-stu-id="668ef-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="668ef-115">`EnumMethodSemantics`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="668ef-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="668ef-116">Il n’y a pas d’événements ou de propriétés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="668ef-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="668ef-117">Dans ce `pcEventProp` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="668ef-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="668ef-118">Notes </span><span class="sxs-lookup"><span data-stu-id="668ef-118">Remarks</span></span>  
 <span data-ttu-id="668ef-119">De nombreux types courants d’exécution de langue définissent les événements *de propriété* `Changed` `On`et les méthodes de *propriété* `Changed` liées à leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="668ef-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="668ef-120">Par exemple, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> le type <xref:System.Windows.Forms.Control.Font%2A> définit <xref:System.Windows.Forms.Control.FontChanged> une propriété, <xref:System.Windows.Forms.Control.OnFontChanged%2A> un événement et une méthode.</span><span class="sxs-lookup"><span data-stu-id="668ef-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="668ef-121">La méthode d’accesseur défini de la <xref:System.Windows.Forms.Control.Font%2A> méthode des appels <xref:System.Windows.Forms.Control.OnFontChanged%2A> de propriété, qui à son tour soulève l’événement. <xref:System.Windows.Forms.Control.FontChanged></span><span class="sxs-lookup"><span data-stu-id="668ef-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="668ef-122">Vous appelez `EnumMethodSemantics` en utilisant le <xref:System.Windows.Forms.Control.OnFontChanged%2A> MethodDef <xref:System.Windows.Forms.Control.Font%2A> pour obtenir <xref:System.Windows.Forms.Control.FontChanged> des références à la propriété et l’événement.</span><span class="sxs-lookup"><span data-stu-id="668ef-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="668ef-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="668ef-123">Requirements</span></span>  
 <span data-ttu-id="668ef-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="668ef-125">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="668ef-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="668ef-126">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="668ef-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="668ef-127">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="668ef-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668ef-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="668ef-128">See also</span></span>

- [<span data-ttu-id="668ef-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="668ef-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="668ef-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="668ef-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
