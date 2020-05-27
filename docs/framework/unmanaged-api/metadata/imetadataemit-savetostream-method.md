---
title: IMetaDataEmit::SaveToStream, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 87e00a69643b6bc403188fb0fdb6f9e3f3d82115
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003873"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="8231d-102">IMetaDataEmit::SaveToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="8231d-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="8231d-103">Enregistre toutes les métadonnées dans la portée actuelle dans le spécifié `IStream` .</span><span class="sxs-lookup"><span data-stu-id="8231d-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8231d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8231d-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8231d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8231d-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="8231d-106">dans Flux accessible en écriture dans lequel effectuer l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="8231d-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8231d-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="8231d-107">[in] Reserved.</span></span> <span data-ttu-id="8231d-108">Doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="8231d-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8231d-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8231d-109">Requirements</span></span>  
 <span data-ttu-id="8231d-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8231d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8231d-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8231d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8231d-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8231d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8231d-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8231d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8231d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8231d-114">See also</span></span>

- [<span data-ttu-id="8231d-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8231d-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8231d-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="8231d-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
