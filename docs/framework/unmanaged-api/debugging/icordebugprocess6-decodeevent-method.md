---
title: ICorDebugProcess6::DecodeEvent, méthode
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178579"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="d5093-102">ICorDebugProcess6::DecodeEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="d5093-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="d5093-103">Décode les événements de débogage managés qui ont été encapsulés dans la charge utile des événements de débogage d'exception native conçus à cet effet.</span><span class="sxs-lookup"><span data-stu-id="d5093-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5093-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5093-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5093-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5093-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="d5093-106">[in] Pointeur vers un tableau d'octets issu d'un événement de débogage d'exception native qui contient des informations sur un événement de débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d5093-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="d5093-107">[in] Nombre d'éléments dans le tableau d'octets `pRecord`.</span><span class="sxs-lookup"><span data-stu-id="d5093-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="d5093-108">[dans] Un membre [corDebugRecordFormat](cordebugrecordformat-enumeration.md) énumération qui spécifie le format de l’événement de débogé non galé.</span><span class="sxs-lookup"><span data-stu-id="d5093-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d5093-109">[in] Champ de bits qui dépend de l'architecture cible et qui spécifie des informations supplémentaires sur l'événement de débogage.</span><span class="sxs-lookup"><span data-stu-id="d5093-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="d5093-110">Pour les systèmes Windows, il peut être membre du recensement [de CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="d5093-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="d5093-111">[in] Identificateur de système d'exploitation du thread sur lequel l'exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="d5093-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="d5093-112">[out] Un pointeur à l’adresse d’un objet [ICorDebugDebugEvent](icordebugdebugevent-interface.md) qui représente un événement de débogé géré décodé.</span><span class="sxs-lookup"><span data-stu-id="d5093-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5093-113">Notes </span><span class="sxs-lookup"><span data-stu-id="d5093-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5093-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d5093-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5093-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d5093-115">Requirements</span></span>  
 <span data-ttu-id="d5093-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5093-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5093-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5093-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5093-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5093-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5093-119">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5093-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5093-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5093-120">See also</span></span>

- [<span data-ttu-id="d5093-121">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="d5093-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="d5093-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d5093-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
