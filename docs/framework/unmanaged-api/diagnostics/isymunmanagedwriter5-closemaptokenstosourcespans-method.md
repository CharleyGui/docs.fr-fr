---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: b57174f9f76b174927b8f1997beac3dd1482583a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725909"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="c1116-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="c1116-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="c1116-103">Fermez la section de données personnalisées spéciale pour les informations de mappage de l’étendue Token-to-source.</span><span class="sxs-lookup"><span data-stu-id="c1116-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="c1116-104">Une fois fermé, aucune autre information de mappage ne peut être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="c1116-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1116-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1116-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c1116-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1116-106">Return Value</span></span>  

 <span data-ttu-id="c1116-107">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c1116-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1116-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1116-108">Requirements</span></span>  

 <span data-ttu-id="c1116-109">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c1116-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1116-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1116-110">See also</span></span>

- [<span data-ttu-id="c1116-111">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="c1116-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
