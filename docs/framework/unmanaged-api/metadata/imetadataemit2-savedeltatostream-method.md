---
title: IMetaDataEmit2::SaveDeltaToStream, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: a8f46871dde4c664a502c261fc882f3badf0f362
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492747"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="b775e-102">IMetaDataEmit2::SaveDeltaToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="b775e-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="b775e-103">Enregistre les modifications de la session de modification et de continuation actuelle dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="b775e-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b775e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b775e-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b775e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b775e-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="b775e-106">dans Pointeur d’interface vers le flux accessible en écriture dans lequel enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="b775e-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="b775e-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="b775e-107">[in] Reserved.</span></span> <span data-ttu-id="b775e-108">Cette valeur doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="b775e-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b775e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b775e-109">Requirements</span></span>  
 <span data-ttu-id="b775e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b775e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b775e-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b775e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b775e-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b775e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b775e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b775e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b775e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b775e-114">See also</span></span>

- [<span data-ttu-id="b775e-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b775e-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b775e-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b775e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
