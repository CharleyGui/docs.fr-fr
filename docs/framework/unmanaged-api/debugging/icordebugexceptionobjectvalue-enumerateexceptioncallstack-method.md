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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a58a62dbcd69d1847ab5a0b0109fe4eea53a4f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754230"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="5475b-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="5475b-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="5475b-103">Obtient un énumérateur pour la pile des appels incorporée dans un objet d’exception.</span><span class="sxs-lookup"><span data-stu-id="5475b-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5475b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5475b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5475b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5475b-105">Parameters</span></span>  
 <span data-ttu-id="5475b-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="5475b-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="5475b-107">[out] Un pointeur vers l’adresse d’un [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objet d’interface qui est un énumérateur de trace de pile pour un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="5475b-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5475b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5475b-108">Remarks</span></span>  
 <span data-ttu-id="5475b-109">Si aucune information de pile d’appel n’est disponible, la méthode retourne `S_OK`, et [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) est un énumérateur valid avec une longueur égale à 0.</span><span class="sxs-lookup"><span data-stu-id="5475b-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="5475b-110">Si la méthode ne peut pas récupérer les informations de trace de pile, la valeur de retour est `E_FAIL` et aucun énumérateur n’est retourné.</span><span class="sxs-lookup"><span data-stu-id="5475b-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="5475b-111">Le [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objet est chargé de décodage des données de trace de pile de le `_stackTrace` champ de l’objet exception.</span><span class="sxs-lookup"><span data-stu-id="5475b-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5475b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5475b-112">Requirements</span></span>  
 <span data-ttu-id="5475b-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5475b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5475b-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5475b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5475b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5475b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5475b-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5475b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5475b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5475b-117">See also</span></span>

- [<span data-ttu-id="5475b-118">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="5475b-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="5475b-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5475b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
