---
title: IMetaDataTables2::GetMetaDataStorage, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 775b3919d1468f26fc3c374dd8ca143aa17853ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708736"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="5e802-102">IMetaDataTables2::GetMetaDataStorage, méthode</span><span class="sxs-lookup"><span data-stu-id="5e802-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>

<span data-ttu-id="5e802-103">Obtient la taille et le contenu des métadonnées stockées dans la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5e802-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e802-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e802-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e802-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e802-105">Parameters</span></span>  

 `ppvMd`  
 <span data-ttu-id="5e802-106">[in, out] Pointeur vers une section de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5e802-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="5e802-107">à Taille du flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5e802-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e802-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e802-108">Requirements</span></span>  

 <span data-ttu-id="5e802-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e802-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e802-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5e802-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e802-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e802-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e802-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e802-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e802-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e802-113">See also</span></span>

- [<span data-ttu-id="5e802-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="5e802-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="5e802-115">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="5e802-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
