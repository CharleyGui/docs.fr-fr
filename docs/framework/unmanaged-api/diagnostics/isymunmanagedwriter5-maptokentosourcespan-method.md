---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: e4b09e6d89b3ba8ba3bf7e149d31a14a74b945b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723933"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="ae0f7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="ae0f7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>

<span data-ttu-id="ae0f7-103">Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="ae0f7-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="ae0f7-104">Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae0f7-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0f7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae0f7-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0f7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae0f7-106">Parameters</span></span>  
  
|<span data-ttu-id="ae0f7-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="ae0f7-107">Parameter</span></span>|<span data-ttu-id="ae0f7-108">Description</span><span class="sxs-lookup"><span data-stu-id="ae0f7-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="ae0f7-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ae0f7-109">Return Value</span></span>  

 <span data-ttu-id="ae0f7-110">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ae0f7-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0f7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae0f7-111">Requirements</span></span>  

 <span data-ttu-id="ae0f7-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ae0f7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0f7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae0f7-113">See also</span></span>

- [<span data-ttu-id="ae0f7-114">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="ae0f7-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
