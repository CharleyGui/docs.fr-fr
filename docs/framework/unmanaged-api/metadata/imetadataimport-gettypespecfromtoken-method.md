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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7e060d2f72609b470dbd5060746a1458f5eed9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782312"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="6dba8-102">IMetaDataImport::GetTypeSpecFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="6dba8-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="6dba8-103">Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="6dba8-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dba8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dba8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dba8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6dba8-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="6dba8-106">[in] Le jeton TypeSpec associé à la signature de métadonnées demandées.</span><span class="sxs-lookup"><span data-stu-id="6dba8-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="6dba8-107">[out] Pointeur vers la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="6dba8-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="6dba8-108">[out] La taille, en octets, de la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6dba8-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dba8-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6dba8-109">Return Value</span></span>  
 <span data-ttu-id="6dba8-110">HRESULT qui indique la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="6dba8-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="6dba8-111">Échecs peuvent être testés avec la macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="6dba8-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dba8-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6dba8-112">Requirements</span></span>  
 <span data-ttu-id="6dba8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dba8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dba8-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6dba8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dba8-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6dba8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6dba8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dba8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dba8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dba8-117">See also</span></span>

- [<span data-ttu-id="6dba8-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6dba8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6dba8-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6dba8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
