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
ms.openlocfilehash: 2a8200f942405395429db182b7501a07fc1f930a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212319"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="5c331-102">ICorDebugModule3::CreateReaderForInMemorySymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="5c331-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="5c331-103">Crée un lecteur de symboles de débogage pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="5c331-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c331-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c331-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c331-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c331-105">Parameters</span></span>  
 <span data-ttu-id="5c331-106">riid</span><span class="sxs-lookup"><span data-stu-id="5c331-106">riid</span></span>  
 <span data-ttu-id="5c331-107">dans IID de l’interface COM à retourner.</span><span class="sxs-lookup"><span data-stu-id="5c331-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="5c331-108">En règle générale, il s’agit d’une [interface ISymUnmanagedReader](../diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5c331-108">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="5c331-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="5c331-109">ppObj</span></span>  
 <span data-ttu-id="5c331-110">à Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="5c331-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c331-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5c331-111">Return Value</span></span>  
 <span data-ttu-id="5c331-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c331-112">S_OK</span></span>  
 <span data-ttu-id="5c331-113">Le lecteur a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="5c331-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="5c331-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="5c331-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="5c331-115">Le module n’est pas un module en mémoire ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="5c331-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="5c331-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c331-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="5c331-117">Les symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.</span><span class="sxs-lookup"><span data-stu-id="5c331-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="5c331-118">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="5c331-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5c331-119">Impossible de créer le lecteur.</span><span class="sxs-lookup"><span data-stu-id="5c331-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c331-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c331-120">Remarks</span></span>  
 <span data-ttu-id="5c331-121">Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules en mémoire (non dynamiques), mais uniquement une fois que les symboles sont disponibles pour la première fois (indiqué par le rappel de la [méthode UpdateModuleSymbols,](icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="5c331-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="5c331-122">Cette méthode retourne une nouvelle instance de lecteur à chaque fois qu’elle est appelée (comme [CComPtrBase :: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="5c331-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="5c331-123">Par conséquent, le débogueur doit mettre en cache le résultat et demander une nouvelle instance uniquement lorsque les données sous-jacentes ont été modifiées (autrement dit, lors de la réception d’un rappel de [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="5c331-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="5c331-124">Les modules dynamiques n’ont aucun symbole disponible tant que le premier type n’a pas été chargé (comme indiqué par le rappel de la [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="5c331-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c331-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5c331-125">Requirements</span></span>  
 <span data-ttu-id="5c331-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c331-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c331-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c331-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c331-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c331-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c331-129">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5c331-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c331-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c331-130">See also</span></span>

- [<span data-ttu-id="5c331-131">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="5c331-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="5c331-132">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="5c331-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="5c331-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5c331-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
