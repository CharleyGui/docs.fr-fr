---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975964"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="ad5e1-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="ad5e1-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="ad5e1-103">Obtient un énumérateur de la pile des appels incorporée dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="ad5e1-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad5e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad5e1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad5e1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad5e1-105">Parameters</span></span>  
 <span data-ttu-id="ad5e1-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="ad5e1-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="ad5e1-107">à Pointeur vers l’adresse d’un objet d’interface [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) qui est un énumérateur de trace de la pile pour un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="ad5e1-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad5e1-108">Notes </span><span class="sxs-lookup"><span data-stu-id="ad5e1-108">Remarks</span></span>  
 <span data-ttu-id="ad5e1-109">Si aucune information sur la pile des appels n’est disponible `S_OK`, la méthode retourne, et [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) est un énumérateur valide dont la longueur est égale à 0.</span><span class="sxs-lookup"><span data-stu-id="ad5e1-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="ad5e1-110">Si la méthode ne peut pas récupérer les informations de trace de la pile, `E_FAIL` la valeur de retour est et aucun énumérateur n’est retourné.</span><span class="sxs-lookup"><span data-stu-id="ad5e1-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="ad5e1-111">L’objet [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) est chargé de décoder les données de trace de `_stackTrace` la pile à partir du champ de l’objet exception.</span><span class="sxs-lookup"><span data-stu-id="ad5e1-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad5e1-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ad5e1-112">Requirements</span></span>  
 <span data-ttu-id="ad5e1-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad5e1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad5e1-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad5e1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad5e1-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad5e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad5e1-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad5e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad5e1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad5e1-117">See also</span></span>

- [<span data-ttu-id="ad5e1-118">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="ad5e1-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="ad5e1-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ad5e1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
