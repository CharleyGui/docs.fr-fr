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
ms.openlocfilehash: 6596689af6533bb00f41b0d03805b3383ae8c3cc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792951"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="c8d24-102">ICorDebugModule3::CreateReaderForInMemorySymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="c8d24-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="c8d24-103">Crée un lecteur de symboles de débogage pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="c8d24-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8d24-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8d24-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="c8d24-105">Parameters</span></span>  
 <span data-ttu-id="c8d24-106">riid</span><span class="sxs-lookup"><span data-stu-id="c8d24-106">riid</span></span>  
 <span data-ttu-id="c8d24-107">dans IID de l’interface COM à retourner.</span><span class="sxs-lookup"><span data-stu-id="c8d24-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="c8d24-108">En règle générale, il s’agit d’une [interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c8d24-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="c8d24-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="c8d24-109">ppObj</span></span>  
 <span data-ttu-id="c8d24-110">à Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="c8d24-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8d24-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c8d24-111">Return Value</span></span>  
 <span data-ttu-id="c8d24-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8d24-112">S_OK</span></span>  
 <span data-ttu-id="c8d24-113">Le lecteur a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="c8d24-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="c8d24-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="c8d24-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="c8d24-115">Le module n’est pas un module en mémoire ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="c8d24-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="c8d24-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8d24-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="c8d24-117">Les symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.</span><span class="sxs-lookup"><span data-stu-id="c8d24-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="c8d24-118">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="c8d24-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c8d24-119">Impossible de créer le lecteur.</span><span class="sxs-lookup"><span data-stu-id="c8d24-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8d24-120">Notes</span><span class="sxs-lookup"><span data-stu-id="c8d24-120">Remarks</span></span>  
 <span data-ttu-id="c8d24-121">Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules en mémoire (non dynamiques), mais uniquement une fois que les symboles sont disponibles pour la première fois (indiqué par le rappel de la [méthode UpdateModuleSymbols,](icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="c8d24-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="c8d24-122">Cette méthode retourne une nouvelle instance de lecteur à chaque fois qu’elle est appelée (comme [CComPtrBase :: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="c8d24-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="c8d24-123">Par conséquent, le débogueur doit mettre en cache le résultat et demander une nouvelle instance uniquement lorsque les données sous-jacentes ont été modifiées (autrement dit, lors de la réception d’un rappel de [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="c8d24-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="c8d24-124">Les modules dynamiques n’ont aucun symbole disponible tant que le premier type n’a pas été chargé (comme indiqué par le rappel de la [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="c8d24-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8d24-125">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c8d24-125">Requirements</span></span>  
 <span data-ttu-id="c8d24-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8d24-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8d24-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8d24-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8d24-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8d24-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8d24-129">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c8d24-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d24-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8d24-130">See also</span></span>

- [<span data-ttu-id="c8d24-131">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="c8d24-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c8d24-132">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="c8d24-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="c8d24-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c8d24-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
