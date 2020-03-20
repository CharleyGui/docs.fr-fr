---
title: IMetaDataImport::GetTypeSpecFromToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175315"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="63326-102">IMetaDataImport::GetTypeSpecFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="63326-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="63326-103">Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="63326-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63326-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63326-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63326-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63326-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="63326-106">[dans] Le jeton TypeSpec associé à la signature des métadonnées demandées.</span><span class="sxs-lookup"><span data-stu-id="63326-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="63326-107">[out] Un pointeur à la signature des métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="63326-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="63326-108">[out] La taille, dans les octets, de la signature des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="63326-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63326-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="63326-109">Return Value</span></span>  
 <span data-ttu-id="63326-110">Un HRESULT qui indique le succès ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="63326-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="63326-111">Les défaillances peuvent être testées avec la macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="63326-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63326-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63326-112">Requirements</span></span>  
 <span data-ttu-id="63326-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63326-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63326-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="63326-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63326-115">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63326-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63326-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63326-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63326-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63326-117">See also</span></span>

- [<span data-ttu-id="63326-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="63326-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="63326-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="63326-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
