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
ms.openlocfilehash: 67abdfd8f8c67299eae757533f20df69392f25b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729185"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="e2696-102">IMetaDataImport::GetSigFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="e2696-102">IMetaDataImport::GetSigFromToken Method</span></span>

<span data-ttu-id="e2696-103">Obtient la signature de métadonnées binaires associée au jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2696-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2696-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2696-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2696-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2696-105">Parameters</span></span>  

 `mdSig`  
 <span data-ttu-id="e2696-106">dans Jeton pour lequel retourner la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="e2696-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="e2696-107">à Pointeur vers la signature de métadonnées retournée.</span><span class="sxs-lookup"><span data-stu-id="e2696-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="e2696-108">à Taille en octets de la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="e2696-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2696-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e2696-109">Requirements</span></span>  

 <span data-ttu-id="e2696-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2696-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2696-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2696-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2696-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2696-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2696-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2696-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2696-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2696-114">See also</span></span>

- [<span data-ttu-id="e2696-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e2696-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e2696-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e2696-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
