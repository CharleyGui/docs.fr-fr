---
title: ICorDebugManagedCallback::UpdateModuleSymbols, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 1615d00a9a25cd2f4aa7d9b84de54b5e7670a3fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730567"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="0968a-102">ICorDebugManagedCallback::UpdateModuleSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="0968a-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>

<span data-ttu-id="0968a-103">Notifie le débogueur que les symboles d’un module common language runtime ont changé.</span><span class="sxs-lookup"><span data-stu-id="0968a-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0968a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0968a-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0968a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0968a-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="0968a-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le module dans lequel les symboles ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="0968a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="0968a-107">dans Pointeur vers un objet ICorDebugModule qui représente le module dans lequel les symboles ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="0968a-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="0968a-108">dans Pointeur vers un objet COM Win32 `IStream` qui contient les symboles modifiés.</span><span class="sxs-lookup"><span data-stu-id="0968a-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0968a-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="0968a-109">Remarks</span></span>  

 <span data-ttu-id="0968a-110">Cette méthode offre la possibilité de mettre à jour la vue du débogueur des symboles d’un module en appelant [ISymUnmanagedReader :: UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ou [ISymUnmanagedReader :: ReplaceSymbolStore,](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="0968a-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="0968a-111">Ce rappel peut se produire plusieurs fois pour le même module.</span><span class="sxs-lookup"><span data-stu-id="0968a-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="0968a-112">Un débogueur doit tenter de lier des points d’arrêt de niveau source non liés.</span><span class="sxs-lookup"><span data-stu-id="0968a-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0968a-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0968a-113">Requirements</span></span>  

 <span data-ttu-id="0968a-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0968a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0968a-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0968a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0968a-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0968a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0968a-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0968a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0968a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0968a-118">See also</span></span>

- [<span data-ttu-id="0968a-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0968a-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
