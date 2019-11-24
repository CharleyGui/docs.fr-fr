---
title: IMetaDataImport::GetEventProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437577"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="91ac6-102">IMetaDataImport::GetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="91ac6-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="91ac6-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span><span class="sxs-lookup"><span data-stu-id="91ac6-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ac6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91ac6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ac6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91ac6-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="91ac6-106">[in] The event metadata token representing the event to get metadata for.</span><span class="sxs-lookup"><span data-stu-id="91ac6-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="91ac6-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="91ac6-108">[out] The name of the event referenced by `ev`.</span><span class="sxs-lookup"><span data-stu-id="91ac6-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="91ac6-109">[in] The requested length in wide characters of `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="91ac6-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="91ac6-110">[out] The returned length in wide characters of `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="91ac6-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="91ac6-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="91ac6-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="91ac6-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="91ac6-114">[out] A pointer to the metadata token representing the method that raises the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="91ac6-115">[out] An array of token pointers to other methods associated with the event.</span><span class="sxs-lookup"><span data-stu-id="91ac6-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="91ac6-116">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="91ac6-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="91ac6-117">[out] The number of tokens returned in `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="91ac6-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ac6-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="91ac6-118">Requirements</span></span>  
 <span data-ttu-id="91ac6-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ac6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ac6-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="91ac6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91ac6-121">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91ac6-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91ac6-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ac6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ac6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91ac6-123">See also</span></span>

- [<span data-ttu-id="91ac6-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="91ac6-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="91ac6-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="91ac6-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
