---
title: ICorDebugMDA::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 6a6769265a2e140f1fa001bb8240bc5d4bd76018
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213671"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="1364a-102">ICorDebugMDA::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="1364a-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="1364a-103">Obtient une chaîne contenant le nom de l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1364a-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1364a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1364a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1364a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1364a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1364a-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="1364a-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1364a-107">à Pointeur vers la longueur du nom.</span><span class="sxs-lookup"><span data-stu-id="1364a-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1364a-108">à Tableau dans lequel stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="1364a-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1364a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="1364a-109">Remarks</span></span>  
 <span data-ttu-id="1364a-110">Les noms MDA sont des valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="1364a-110">MDA names are unique values.</span></span> <span data-ttu-id="1364a-111">La `GetName` méthode est une alternative pratique en matière de performances à l’obtention du flux XML et à l’extraction du nom du flux en fonction du schéma.</span><span class="sxs-lookup"><span data-stu-id="1364a-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1364a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1364a-112">Requirements</span></span>  
 <span data-ttu-id="1364a-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1364a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1364a-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1364a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1364a-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1364a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1364a-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1364a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1364a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1364a-117">See also</span></span>

- [<span data-ttu-id="1364a-118">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="1364a-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="1364a-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="1364a-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
