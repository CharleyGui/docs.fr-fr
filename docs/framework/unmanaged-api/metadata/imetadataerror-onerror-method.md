---
title: IMetaDataError::OnError, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177400"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="e5655-102">IMetaDataError::OnError, méthode</span><span class="sxs-lookup"><span data-stu-id="e5655-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="e5655-103">Fournit la notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e5655-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5655-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5655-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5655-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5655-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="e5655-106">[dans] La valeur d’erreur HRESULT est revenue à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="e5655-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="e5655-107">[dans] Les métadonnées symboliques de l’objet de code qui a été fusionné lorsque l’erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e5655-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5655-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5655-108">Requirements</span></span>  
 <span data-ttu-id="e5655-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5655-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5655-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="e5655-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5655-111">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5655-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5655-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5655-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5655-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5655-113">See also</span></span>

- [<span data-ttu-id="e5655-114">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="e5655-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
