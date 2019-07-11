---
title: IMetaDataTables::GetStringHeapSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b842fb4d0853f473ae8e237a42e800cf0af8dc11
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781388"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="05d60-102">IMetaDataTables::GetStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="05d60-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="05d60-103">Obtient la taille, en octets, du tas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="05d60-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d60-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d60-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05d60-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="05d60-106">[out] Pointeur vers la taille, en octets, du tas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="05d60-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d60-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05d60-107">Requirements</span></span>  
 <span data-ttu-id="05d60-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d60-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d60-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05d60-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05d60-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05d60-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05d60-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d60-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d60-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d60-112">See also</span></span>

- [<span data-ttu-id="05d60-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="05d60-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="05d60-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="05d60-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
