---
title: ICorDebugModule3::CreateReaderForInMemorySymbols, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 44f4c59f95c28f9982d67875584e2f9803c0ed3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709568"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="efdb7-102">ICorDebugModule3::CreateReaderForInMemorySymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="efdb7-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>

<span data-ttu-id="efdb7-103">Crée un lecteur de symboles de débogage pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="efdb7-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efdb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efdb7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="efdb7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efdb7-105">Parameters</span></span>  

 <span data-ttu-id="efdb7-106">riid</span><span class="sxs-lookup"><span data-stu-id="efdb7-106">riid</span></span>  
 <span data-ttu-id="efdb7-107">dans IID de l’interface COM à retourner.</span><span class="sxs-lookup"><span data-stu-id="efdb7-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="efdb7-108">En règle générale, il s’agit d’une [interface ISymUnmanagedReader](../diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="efdb7-108">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="efdb7-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="efdb7-109">ppObj</span></span>  
 <span data-ttu-id="efdb7-110">à Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="efdb7-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efdb7-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="efdb7-111">Return Value</span></span>  

 <span data-ttu-id="efdb7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="efdb7-112">S_OK</span></span>  
 <span data-ttu-id="efdb7-113">Le lecteur a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="efdb7-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="efdb7-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="efdb7-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="efdb7-115">Le module n’est pas un module en mémoire ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="efdb7-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="efdb7-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efdb7-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="efdb7-117">Les symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.</span><span class="sxs-lookup"><span data-stu-id="efdb7-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="efdb7-118">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="efdb7-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="efdb7-119">Impossible de créer le lecteur.</span><span class="sxs-lookup"><span data-stu-id="efdb7-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efdb7-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="efdb7-120">Remarks</span></span>  

 <span data-ttu-id="efdb7-121">Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules en mémoire (non dynamiques), mais uniquement une fois que les symboles sont disponibles pour la première fois (indiqué par le rappel de la [méthode UpdateModuleSymbols,](icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="efdb7-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="efdb7-122">Cette méthode retourne une nouvelle instance de lecteur à chaque fois qu’elle est appelée (comme [CComPtrBase :: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="efdb7-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="efdb7-123">Par conséquent, le débogueur doit mettre en cache le résultat et demander une nouvelle instance uniquement lorsque les données sous-jacentes ont été modifiées (autrement dit, lors de la réception d’un rappel de [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="efdb7-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="efdb7-124">Les modules dynamiques n’ont aucun symbole disponible tant que le premier type n’a pas été chargé (comme indiqué par le rappel de la [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="efdb7-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efdb7-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="efdb7-125">Requirements</span></span>  

 <span data-ttu-id="efdb7-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efdb7-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efdb7-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efdb7-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efdb7-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efdb7-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efdb7-129">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="efdb7-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdb7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efdb7-130">See also</span></span>

- [<span data-ttu-id="efdb7-131">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="efdb7-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="efdb7-132">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="efdb7-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="efdb7-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="efdb7-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
