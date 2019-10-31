---
title: ISymUnmanagedWriter5, interface
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 18371b6aefb002f5adf27d43f85194c6c35f6ef5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121641"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="8d148-102">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="8d148-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="8d148-103">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="8d148-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d148-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d148-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="8d148-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8d148-105">Methods</span></span>  
 <span data-ttu-id="8d148-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d148-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="8d148-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="8d148-107">Method</span></span>|<span data-ttu-id="8d148-108">Description</span><span class="sxs-lookup"><span data-stu-id="8d148-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d148-109">CloseMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="8d148-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="8d148-110">Fermez la section de données personnalisées spéciale pour les informations de mappage de l’étendue Token-to-source.</span><span class="sxs-lookup"><span data-stu-id="8d148-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="8d148-111">Une fois fermé, aucune autre information de mappage ne peut être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="8d148-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="8d148-112">MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="8d148-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="8d148-113">Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d148-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="8d148-114">Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d148-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="8d148-115">OpenMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="8d148-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="8d148-116">Ouvrez une section de données personnalisées spéciale pour émettre des informations de mappage de jeton-à-source dans.</span><span class="sxs-lookup"><span data-stu-id="8d148-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="8d148-117">L’ouverture de cette section quand une méthode est déjà ouverte, ou vice versa, est une erreur.</span><span class="sxs-lookup"><span data-stu-id="8d148-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d148-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="8d148-118">Requirements</span></span>  
 <span data-ttu-id="8d148-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8d148-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d148-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d148-120">See also</span></span>

- [<span data-ttu-id="8d148-121">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="8d148-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8d148-122">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="8d148-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
