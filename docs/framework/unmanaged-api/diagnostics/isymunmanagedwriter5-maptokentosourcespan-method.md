---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501675"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="98648-102">ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="98648-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="98648-103">Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="98648-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="98648-104">Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="98648-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98648-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98648-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98648-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98648-106">Parameters</span></span>  
  
|<span data-ttu-id="98648-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="98648-107">Parameter</span></span>|<span data-ttu-id="98648-108">Description</span><span class="sxs-lookup"><span data-stu-id="98648-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="98648-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="98648-109">Return Value</span></span>  
 <span data-ttu-id="98648-110">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="98648-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98648-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98648-111">Requirements</span></span>  
 <span data-ttu-id="98648-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="98648-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98648-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98648-113">See also</span></span>

- [<span data-ttu-id="98648-114">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="98648-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
