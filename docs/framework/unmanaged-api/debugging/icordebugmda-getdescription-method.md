---
title: ICorDebugMDA::GetDescription, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da57ecf0c153d902322798e1927c995a34cb93d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761990"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="8c02d-102">ICorDebugMDA::GetDescription, méthode</span><span class="sxs-lookup"><span data-stu-id="8c02d-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="8c02d-103">Obtient une chaîne qui contient la description de l’assistant débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8c02d-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c02d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c02d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c02d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c02d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8c02d-106">[in] La taille de la mémoire tampon de chaîne qui stockera la description.</span><span class="sxs-lookup"><span data-stu-id="8c02d-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8c02d-107">[out] Pointeur vers le nombre d’octets retournés dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8c02d-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c02d-108">[out] Un mémoire tampon de chaîne qui contient la description de l’Assistant Débogage MANAGÉ.</span><span class="sxs-lookup"><span data-stu-id="8c02d-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c02d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8c02d-109">Remarks</span></span>  
 <span data-ttu-id="8c02d-110">La chaîne peut être de longueur zéro.</span><span class="sxs-lookup"><span data-stu-id="8c02d-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c02d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c02d-111">Requirements</span></span>  
 <span data-ttu-id="8c02d-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c02d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c02d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c02d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c02d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c02d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c02d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c02d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c02d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c02d-116">See also</span></span>

- [<span data-ttu-id="8c02d-117">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="8c02d-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="8c02d-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="8c02d-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
