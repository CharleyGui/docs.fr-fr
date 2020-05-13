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
ms.openlocfilehash: 522e992e6d7e9a64f7590bbec0e9106e0e1f8f47
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212137"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="558f0-102">ICorDebugMDA::GetDescription, méthode</span><span class="sxs-lookup"><span data-stu-id="558f0-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="558f0-103">Obtient une chaîne contenant la description de l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="558f0-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="558f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="558f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="558f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="558f0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="558f0-106">dans Taille de la mémoire tampon de chaîne qui stocke la description.</span><span class="sxs-lookup"><span data-stu-id="558f0-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="558f0-107">à Pointeur vers le nombre d’octets retournés dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="558f0-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="558f0-108">à Mémoire tampon de chaîne contenant la description de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="558f0-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="558f0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="558f0-109">Remarks</span></span>  
 <span data-ttu-id="558f0-110">La longueur de la chaîne peut être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="558f0-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="558f0-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="558f0-111">Requirements</span></span>  
 <span data-ttu-id="558f0-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="558f0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="558f0-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="558f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="558f0-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="558f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="558f0-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="558f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558f0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="558f0-116">See also</span></span>

- [<span data-ttu-id="558f0-117">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="558f0-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="558f0-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="558f0-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
