---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 82b46ea315009b65254735d44e355154b83b22e2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609493"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="be2bf-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="be2bf-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="be2bf-103">Ouvrez une section de données personnalisées spéciale pour émettre des informations de mappage de jeton-à-source dans.</span><span class="sxs-lookup"><span data-stu-id="be2bf-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="be2bf-104">L’ouverture de cette section quand une méthode est déjà ouverte, ou vice versa, est une erreur.</span><span class="sxs-lookup"><span data-stu-id="be2bf-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be2bf-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be2bf-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be2bf-106">Return Value</span></span>  
 <span data-ttu-id="be2bf-107">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="be2bf-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2bf-108">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="be2bf-108">Requirements</span></span>  
 <span data-ttu-id="be2bf-109">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be2bf-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2bf-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be2bf-110">See also</span></span>

- [<span data-ttu-id="be2bf-111">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="be2bf-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
