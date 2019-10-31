---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121626"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="df2a2-102">ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="df2a2-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="df2a2-103">Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="df2a2-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="df2a2-104">Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="df2a2-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df2a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df2a2-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df2a2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df2a2-106">Parameters</span></span>  
  
|<span data-ttu-id="df2a2-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="df2a2-107">Parameter</span></span>|<span data-ttu-id="df2a2-108">Description</span><span class="sxs-lookup"><span data-stu-id="df2a2-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="df2a2-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df2a2-109">Return Value</span></span>  
 <span data-ttu-id="df2a2-110">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="df2a2-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df2a2-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="df2a2-111">Requirements</span></span>  
 <span data-ttu-id="df2a2-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="df2a2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df2a2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df2a2-113">See also</span></span>

- [<span data-ttu-id="df2a2-114">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="df2a2-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
