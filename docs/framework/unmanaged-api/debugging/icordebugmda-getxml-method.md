---
title: ICorDebugMDA::GetXML, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: f80bdffbf5c0ba39980bd27c6e89a368547340c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129810"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="e8577-102">ICorDebugMDA::GetXML, méthode</span><span class="sxs-lookup"><span data-stu-id="e8577-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="e8577-103">Obtient le flux de données XML complet associé à l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e8577-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8577-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8577-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8577-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e8577-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="e8577-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e8577-107">à Pointeur vers la longueur du flux XML.</span><span class="sxs-lookup"><span data-stu-id="e8577-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="e8577-108">à Tableau dans lequel stocker le flux XML.</span><span class="sxs-lookup"><span data-stu-id="e8577-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="e8577-109">Le tableau peut être vide.</span><span class="sxs-lookup"><span data-stu-id="e8577-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8577-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e8577-110">Remarks</span></span>  
 <span data-ttu-id="e8577-111">La méthode `GetXML` peut potentiellement affecter les performances, en fonction de la taille du flux XML associé.</span><span class="sxs-lookup"><span data-stu-id="e8577-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8577-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="e8577-112">Requirements</span></span>  
 <span data-ttu-id="e8577-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8577-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8577-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8577-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8577-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8577-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8577-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8577-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8577-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8577-117">See also</span></span>

- [<span data-ttu-id="e8577-118">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="e8577-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="e8577-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="e8577-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
