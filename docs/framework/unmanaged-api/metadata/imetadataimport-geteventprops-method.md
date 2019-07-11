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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c87f2212c761dc31a75addabca6970c5497aa2a0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782429"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="b36b1-102">IMetaDataImport::GetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b36b1-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="b36b1-103">Obtient les informations de métadonnées pour l’événement représenté par le jeton d’événement spécifié, y compris le type déclarant, l’ajouter et supprimer des méthodes pour les délégués et les indicateurs et autres données associées.</span><span class="sxs-lookup"><span data-stu-id="b36b1-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b36b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b36b1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b36b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b36b1-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="b36b1-106">[in] Le jeton de métadonnées d’événement représentant l’événement pour lequel obtenir les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b36b1-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b36b1-107">[out] Pointeur vers le jeton TypeDef représentant la classe qui déclare l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="b36b1-108">[out] Le nom de l’événement référencé par `ev`.</span><span class="sxs-lookup"><span data-stu-id="b36b1-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="b36b1-109">[in] La longueur demandée en caractères larges de `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b36b1-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="b36b1-110">[out] La longueur retournée en caractères larges de `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b36b1-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="b36b1-111">[out] Un pointeur vers un TypeRef ou TypeDef métadonnées jeton représentant le <xref:System.Delegate> type de l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="b36b1-112">[out] Pointeur vers le jeton de métadonnées qui représente la méthode qui ajoute des gestionnaires pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="b36b1-113">[out] Pointeur vers le jeton de métadonnées qui représente la méthode qui supprime les gestionnaires pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="b36b1-114">[out] Pointeur vers le jeton de métadonnées représentant la méthode qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b36b1-115">[out] Un tableau de pointeurs de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="b36b1-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b36b1-116">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b36b1-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b36b1-117">[out] Le nombre de jetons retournés dans `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b36b1-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b36b1-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b36b1-118">Requirements</span></span>  
 <span data-ttu-id="b36b1-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b36b1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b36b1-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b36b1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b36b1-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b36b1-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b36b1-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b36b1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36b1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b36b1-123">See also</span></span>

- [<span data-ttu-id="b36b1-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b36b1-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b36b1-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b36b1-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
