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
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207656"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="9e7b2-102">ICorDebugMDA::GetXML, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7b2-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="9e7b2-103">Obtient le flux de données XML complet associé à l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9e7b2-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e7b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e7b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e7b2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9e7b2-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="9e7b2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9e7b2-107">à Pointeur vers la longueur du flux XML.</span><span class="sxs-lookup"><span data-stu-id="9e7b2-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="9e7b2-108">à Tableau dans lequel stocker le flux XML.</span><span class="sxs-lookup"><span data-stu-id="9e7b2-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="9e7b2-109">Le tableau peut être vide.</span><span class="sxs-lookup"><span data-stu-id="9e7b2-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e7b2-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e7b2-110">Remarks</span></span>  
 <span data-ttu-id="9e7b2-111">La `GetXML` méthode peut potentiellement affecter les performances, en fonction de la taille du flux XML associé.</span><span class="sxs-lookup"><span data-stu-id="9e7b2-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7b2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9e7b2-112">Requirements</span></span>  
 <span data-ttu-id="9e7b2-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e7b2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7b2-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e7b2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e7b2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e7b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e7b2-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7b2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e7b2-117">See also</span></span>

- [<span data-ttu-id="9e7b2-118">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="9e7b2-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="9e7b2-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="9e7b2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
