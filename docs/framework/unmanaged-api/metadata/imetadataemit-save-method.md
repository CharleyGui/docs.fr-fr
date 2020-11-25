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
ms.openlocfilehash: cef238239417a0a30cd94eaa8bd60968cfa78859
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721996"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="1ac55-102">IMetaDataEmit::Save, méthode</span><span class="sxs-lookup"><span data-stu-id="1ac55-102">IMetaDataEmit::Save Method</span></span>

<span data-ttu-id="1ac55-103">Enregistre toutes les métadonnées de l’étendue actuelle dans le fichier à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1ac55-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ac55-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ac55-105">Parameters</span></span>  

 `wzFile`  
 <span data-ttu-id="1ac55-106">dans Nom du fichier dans lequel enregistrer.</span><span class="sxs-lookup"><span data-stu-id="1ac55-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="1ac55-107">Si cette valeur est null, la copie en mémoire sera enregistrée dans le dernier emplacement utilisé.</span><span class="sxs-lookup"><span data-stu-id="1ac55-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="1ac55-108">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="1ac55-108">[in] Reserved.</span></span> <span data-ttu-id="1ac55-109">Doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="1ac55-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac55-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ac55-110">Requirements</span></span>  

 <span data-ttu-id="1ac55-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac55-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac55-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1ac55-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ac55-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ac55-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ac55-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac55-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ac55-115">See also</span></span>

- [<span data-ttu-id="1ac55-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="1ac55-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1ac55-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="1ac55-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
