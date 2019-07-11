---
title: IMetaDataEmit::Save, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ece16d8dcdc685db960a485cd19261f6b9f2fbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757591"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="02ab2-102">IMetaDataEmit::Save, méthode</span><span class="sxs-lookup"><span data-stu-id="02ab2-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="02ab2-103">Enregistre toutes les métadonnées dans la portée actuelle dans le fichier à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="02ab2-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ab2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02ab2-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02ab2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02ab2-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="02ab2-106">[in] Le nom du fichier à enregistrer dans.</span><span class="sxs-lookup"><span data-stu-id="02ab2-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="02ab2-107">Si cette valeur est null, la copie en mémoire sera enregistrée dans le dernier emplacement qui a été utilisé.</span><span class="sxs-lookup"><span data-stu-id="02ab2-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="02ab2-108">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="02ab2-108">[in] Reserved.</span></span> <span data-ttu-id="02ab2-109">Doit être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="02ab2-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02ab2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="02ab2-110">Requirements</span></span>  
 <span data-ttu-id="02ab2-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02ab2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ab2-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02ab2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02ab2-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02ab2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02ab2-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ab2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ab2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ab2-115">See also</span></span>

- [<span data-ttu-id="02ab2-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="02ab2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="02ab2-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="02ab2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
