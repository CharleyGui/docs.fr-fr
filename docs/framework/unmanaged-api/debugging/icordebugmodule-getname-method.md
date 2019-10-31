---
title: ICorDebugModule::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: b27e7a2cdcbfc3a88a734230118d99c2dd5c700e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129534"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="95150-102">ICorDebugModule::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="95150-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="95150-103">Obtient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="95150-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95150-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95150-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95150-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="95150-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="95150-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="95150-107">dans Pointeur vers la longueur du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="95150-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="95150-108">à Tableau qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="95150-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95150-109">Notes</span><span class="sxs-lookup"><span data-stu-id="95150-109">Remarks</span></span>  
 <span data-ttu-id="95150-110">La méthode `GetName` retourne un HRESULT S_OK si le nom de fichier du module correspond au nom sur le disque.</span><span class="sxs-lookup"><span data-stu-id="95150-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="95150-111">`GetName` retourne une valeur S_FALSE HRESULT si le nom est fabriqué, par exemple pour un module dynamique ou en mémoire.</span><span class="sxs-lookup"><span data-stu-id="95150-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95150-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="95150-112">Requirements</span></span>  
 <span data-ttu-id="95150-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95150-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95150-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95150-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95150-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95150-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95150-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95150-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95150-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95150-117">See also</span></span>
