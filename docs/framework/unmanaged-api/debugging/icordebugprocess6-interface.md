---
title: ICorDebugProcess6, interface
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ba70bab28eeddad6e3cf3c2b82b196a69ce68647
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732604"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="35e94-102">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="35e94-102">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="35e94-103">Étend logiquement l’interface ICorDebugProcess pour activer des fonctionnalités telles que le fractionnement de module virtuel ou le décodage des événements de débogage managés qui sont codés dans des événements de débogage d’exception native.</span><span class="sxs-lookup"><span data-stu-id="35e94-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35e94-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="35e94-104">Methods</span></span>  
  
|<span data-ttu-id="35e94-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-105">Method</span></span>|<span data-ttu-id="35e94-106">Description</span><span class="sxs-lookup"><span data-stu-id="35e94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35e94-107">DecodeEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="35e94-108">Décode les événements de débogage managés qui ont été encapsulés dans la charge utile des événements de débogage d'exception native conçus à cet effet.</span><span class="sxs-lookup"><span data-stu-id="35e94-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="35e94-109">EnableVirtualModuleSplitting, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="35e94-110">Active ou désactive le fractionnement de module virtuel.</span><span class="sxs-lookup"><span data-stu-id="35e94-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="35e94-111">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="35e94-112">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="35e94-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="35e94-113">GetExportStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="35e94-114">Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.</span><span class="sxs-lookup"><span data-stu-id="35e94-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="35e94-115">MarkDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="35e94-116">Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="35e94-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="35e94-117">ProcessStateChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="35e94-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="35e94-118">Informe [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="35e94-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35e94-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="35e94-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35e94-120">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="35e94-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="35e94-121">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="35e94-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e94-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35e94-122">Requirements</span></span>  

 <span data-ttu-id="35e94-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e94-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35e94-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35e94-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35e94-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35e94-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35e94-126">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35e94-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e94-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35e94-127">See also</span></span>

- [<span data-ttu-id="35e94-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="35e94-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="35e94-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="35e94-129">Debugging</span></span>](index.md)
