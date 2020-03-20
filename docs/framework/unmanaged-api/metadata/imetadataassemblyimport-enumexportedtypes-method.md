---
title: IMetaDataAssemblyImport::EnumExportedTypes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176004"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="8d79f-102">IMetaDataAssemblyImport::EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="8d79f-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="8d79f-103">Énumère les types exportés mentionnés dans l’assemblage manifeste dans la portée actuelle des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8d79f-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d79f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d79f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d79f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d79f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8d79f-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="8d79f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8d79f-107">Cela doit être une `EnumExportedTypes` valeur nulle lorsque la méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="8d79f-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="8d79f-108">[out] L’énumération `mdExportedType` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8d79f-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8d79f-109">[dans] Le nombre `mdExportedType` maximum de jetons qui `rExportedTypes` peuvent être placés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="8d79f-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8d79f-110">[out] Le nombre `mdExportedType` de jetons `rExportedTypes`effectivement placés en .</span><span class="sxs-lookup"><span data-stu-id="8d79f-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d79f-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8d79f-111">Return Value</span></span>  
  
|<span data-ttu-id="8d79f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d79f-112">HRESULT</span></span>|<span data-ttu-id="8d79f-113">Description</span><span class="sxs-lookup"><span data-stu-id="8d79f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8d79f-114">`EnumExportedTypes`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8d79f-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8d79f-115">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="8d79f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8d79f-116">Dans ce `pcTokens` cas, est réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="8d79f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d79f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d79f-117">Requirements</span></span>  
 <span data-ttu-id="8d79f-118">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d79f-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d79f-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="8d79f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d79f-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d79f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d79f-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d79f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d79f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d79f-122">See also</span></span>

- [<span data-ttu-id="8d79f-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="8d79f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
