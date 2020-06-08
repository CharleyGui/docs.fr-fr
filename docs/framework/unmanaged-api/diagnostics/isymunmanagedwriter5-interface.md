---
title: ISymUnmanagedWriter5, interface
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493576"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="31f12-102">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="31f12-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="31f12-103">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="31f12-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f12-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31f12-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="31f12-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="31f12-105">Methods</span></span>  
 <span data-ttu-id="31f12-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="31f12-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="31f12-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="31f12-107">Method</span></span>|<span data-ttu-id="31f12-108">Description</span><span class="sxs-lookup"><span data-stu-id="31f12-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31f12-109">CloseMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="31f12-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="31f12-110">Fermez la section de données personnalisées spéciale pour les informations de mappage de l’étendue Token-to-source.</span><span class="sxs-lookup"><span data-stu-id="31f12-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="31f12-111">Une fois fermé, aucune autre information de mappage ne peut être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="31f12-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="31f12-112">MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="31f12-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="31f12-113">Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="31f12-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="31f12-114">Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="31f12-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="31f12-115">OpenMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="31f12-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="31f12-116">Ouvrez une section de données personnalisées spéciale pour émettre des informations de mappage de jeton-à-source dans.</span><span class="sxs-lookup"><span data-stu-id="31f12-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="31f12-117">L’ouverture de cette section quand une méthode est déjà ouverte, ou vice versa, est une erreur.</span><span class="sxs-lookup"><span data-stu-id="31f12-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31f12-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31f12-118">Requirements</span></span>  
 <span data-ttu-id="31f12-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="31f12-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f12-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31f12-120">See also</span></span>

- [<span data-ttu-id="31f12-121">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="31f12-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="31f12-122">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="31f12-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
