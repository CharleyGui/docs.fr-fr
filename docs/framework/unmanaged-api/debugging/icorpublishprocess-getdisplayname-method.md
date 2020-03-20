---
title: ICorPublishProcess::GetDisplayName, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: 77e801b048709949c384f642fc0d0ecb5d7eb512
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178379"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="9cf5c-102">ICorPublishProcess::GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="9cf5c-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="9cf5c-103">Obtient le chemin complet de l’exécutable pour le processus référencé par ce [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cf5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cf5c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9cf5c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9cf5c-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9cf5c-107">[out] Le nombre de personnages `szName` larges retournés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="9cf5c-108">[out] Un tableau pour stocker le nom, y compris le chemin complet, de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="9cf5c-109">Le nom est annulé.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf5c-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9cf5c-110">Requirements</span></span>  
 <span data-ttu-id="9cf5c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf5c-112">**En-tête:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9cf5c-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9cf5c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cf5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cf5c-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf5c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cf5c-115">See also</span></span>

- [<span data-ttu-id="9cf5c-116">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="9cf5c-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
