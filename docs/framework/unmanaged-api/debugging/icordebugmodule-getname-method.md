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
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212540"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="97c9e-102">ICorDebugModule::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="97c9e-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="97c9e-103">Obtient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="97c9e-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97c9e-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97c9e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97c9e-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="97c9e-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="97c9e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="97c9e-107">dans Pointeur vers la longueur du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="97c9e-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="97c9e-108">à Tableau qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="97c9e-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97c9e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="97c9e-109">Remarks</span></span>  
 <span data-ttu-id="97c9e-110">La `GetName` méthode retourne un S_OK HRESULT si le nom de fichier du module correspond au nom sur le disque.</span><span class="sxs-lookup"><span data-stu-id="97c9e-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="97c9e-111">`GetName`retourne un S_FALSE HRESULT si le nom est fabriqué, par exemple pour un module dynamique ou en mémoire.</span><span class="sxs-lookup"><span data-stu-id="97c9e-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c9e-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="97c9e-112">Requirements</span></span>  
 <span data-ttu-id="97c9e-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97c9e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c9e-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97c9e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97c9e-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97c9e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97c9e-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c9e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c9e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97c9e-117">See also</span></span>
