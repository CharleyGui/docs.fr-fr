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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177270"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="8faf9-102">IMetaDataImport::GetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8faf9-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="8faf9-103">Obtient des informations sur les métadonnées pour l’événement représentées par le jeton d’événement spécifié, y compris le type de déclaration, les méthodes d’ajout et de suppression pour les délégués, et tous les drapeaux et autres données associées.</span><span class="sxs-lookup"><span data-stu-id="8faf9-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8faf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8faf9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8faf9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8faf9-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="8faf9-106">[dans] Le jeton des métadonnées de l’événement représentant l’événement pour obtenir des métadonnées pour.</span><span class="sxs-lookup"><span data-stu-id="8faf9-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="8faf9-107">[out] Un pointeur pour le jeton TypeDef représentant la classe qui déclare l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="8faf9-108">[out] Le nom de l’événement référencé par `ev`.</span><span class="sxs-lookup"><span data-stu-id="8faf9-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="8faf9-109">[dans] La longueur demandée `szEvent`en caractères larges de .</span><span class="sxs-lookup"><span data-stu-id="8faf9-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="8faf9-110">[out] La longueur retournée dans `szEvent`de larges caractères de .</span><span class="sxs-lookup"><span data-stu-id="8faf9-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="8faf9-111">[out] Un pointeur vers un jeton de métadonnées <xref:System.Delegate> TypeRef ou TypeDef représentant le type de l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="8faf9-112">[out] Un pointeur sur le jeton des métadonnées représentant la méthode qui ajoute des gestionnaires pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="8faf9-113">[out] Un pointeur sur le jeton des métadonnées représentant la méthode qui supprime les gestionnaires pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="8faf9-114">[out] Un pointeur sur le jeton des métadonnées représentant la méthode qui soulève l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="8faf9-115">[out] Un éventail de pointeurs symboliques à d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="8faf9-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8faf9-116">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="8faf9-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="8faf9-117">[out] Le nombre de jetons `rmdOtherMethod`retournés dans .</span><span class="sxs-lookup"><span data-stu-id="8faf9-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8faf9-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8faf9-118">Requirements</span></span>  
 <span data-ttu-id="8faf9-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8faf9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8faf9-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="8faf9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8faf9-121">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8faf9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8faf9-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8faf9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8faf9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8faf9-123">See also</span></span>

- [<span data-ttu-id="8faf9-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8faf9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8faf9-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8faf9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
