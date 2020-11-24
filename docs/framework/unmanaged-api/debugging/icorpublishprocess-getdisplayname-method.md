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
ms.openlocfilehash: 5a037695892252042d7827165595f7bad0feba56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693162"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="ce88e-102">ICorPublishProcess::GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="ce88e-102">ICorPublishProcess::GetDisplayName Method</span></span>

<span data-ttu-id="ce88e-103">Obtient le chemin d’accès complet de l’exécutable pour le processus référencé par [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ce88e-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce88e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce88e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce88e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce88e-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ce88e-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="ce88e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ce88e-107">à Nombre de caractères larges retournés dans le `szName` tableau.</span><span class="sxs-lookup"><span data-stu-id="ce88e-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="ce88e-108">à Tableau pour stocker le nom, y compris le chemin d’accès complet de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="ce88e-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="ce88e-109">Le nom se termine par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="ce88e-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce88e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce88e-110">Requirements</span></span>  

 <span data-ttu-id="ce88e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce88e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce88e-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ce88e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ce88e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce88e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce88e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce88e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce88e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce88e-115">See also</span></span>

- [<span data-ttu-id="ce88e-116">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="ce88e-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
