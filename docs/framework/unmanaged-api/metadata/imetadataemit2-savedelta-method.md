---
title: IMetaDataEmit2::SaveDelta, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: d3e25f271fc434785e25e7b226ad98f86b5f8dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492783"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="1bdff-102">IMetaDataEmit2::SaveDelta, méthode</span><span class="sxs-lookup"><span data-stu-id="1bdff-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="1bdff-103">Enregistre les modifications de la session de modification et de poursuite en cours dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="1bdff-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bdff-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bdff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bdff-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="1bdff-106">dans Nom de fichier sous lequel enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="1bdff-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="1bdff-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="1bdff-107">[in] Reserved.</span></span> <span data-ttu-id="1bdff-108">Doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="1bdff-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bdff-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bdff-109">Requirements</span></span>  
 <span data-ttu-id="1bdff-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdff-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1bdff-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1bdff-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1bdff-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1bdff-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdff-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bdff-114">See also</span></span>

- [<span data-ttu-id="1bdff-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="1bdff-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="1bdff-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="1bdff-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
