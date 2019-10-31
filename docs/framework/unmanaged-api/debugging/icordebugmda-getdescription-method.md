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
ms.openlocfilehash: bfe77982b88b2fc96dc2846b9db04df28bfc0c38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131450"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="5cc85-102">ICorDebugMDA::GetDescription, méthode</span><span class="sxs-lookup"><span data-stu-id="5cc85-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="5cc85-103">Obtient une chaîne contenant la description de l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5cc85-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cc85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cc85-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cc85-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5cc85-106">dans Taille de la mémoire tampon de chaîne qui stocke la description.</span><span class="sxs-lookup"><span data-stu-id="5cc85-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5cc85-107">à Pointeur vers le nombre d’octets retournés dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5cc85-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5cc85-108">à Mémoire tampon de chaîne contenant la description de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="5cc85-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc85-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5cc85-109">Remarks</span></span>  
 <span data-ttu-id="5cc85-110">La longueur de la chaîne peut être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="5cc85-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc85-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="5cc85-111">Requirements</span></span>  
 <span data-ttu-id="5cc85-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc85-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc85-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cc85-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cc85-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cc85-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cc85-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc85-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cc85-116">See also</span></span>

- [<span data-ttu-id="5cc85-117">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="5cc85-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="5cc85-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="5cc85-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
