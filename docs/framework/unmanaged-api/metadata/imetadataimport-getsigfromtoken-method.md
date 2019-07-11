---
title: IMetaDataImport::GetSigFromToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2060a70e2a3ce355f43ade67e6d6843670e00ad3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778849"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="46811-102">IMetaDataImport::GetSigFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="46811-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="46811-103">Obtient la signature de métadonnées binaires associée au jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="46811-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46811-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46811-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46811-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46811-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="46811-106">[in] Le jeton à retourner pour la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="46811-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="46811-107">[out] Pointeur vers la signature de métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="46811-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="46811-108">[out] La taille en octets de la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="46811-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46811-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="46811-109">Requirements</span></span>  
 <span data-ttu-id="46811-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46811-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46811-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="46811-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46811-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46811-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46811-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46811-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46811-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46811-114">See also</span></span>

- [<span data-ttu-id="46811-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="46811-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="46811-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="46811-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
