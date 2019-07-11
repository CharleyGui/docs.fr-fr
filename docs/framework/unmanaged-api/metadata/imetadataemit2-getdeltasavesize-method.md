---
title: IMetaDataEmit2::GetDeltaSaveSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b0a190ce57091434006421e6d8551c78cbe66b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777166"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="5ed3a-102">IMetaDataEmit2::GetDeltaSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="5ed3a-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="5ed3a-103">Obtient une valeur indiquant toute modification de la taille des métadonnées qui résulte de la session active modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="5ed3a-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ed3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ed3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ed3a-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="5ed3a-106">[in] Parmi les [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) valeurs indiquant le niveau de précision que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="5ed3a-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="5ed3a-107">Pour le .NET Framework version 2.0, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="5ed3a-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="5ed3a-108">[out] La modification de la taille des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5ed3a-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed3a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ed3a-109">Requirements</span></span>  
 <span data-ttu-id="5ed3a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed3a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed3a-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5ed3a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ed3a-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ed3a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ed3a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed3a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed3a-114">See also</span></span>

- [<span data-ttu-id="5ed3a-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="5ed3a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="5ed3a-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="5ed3a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
