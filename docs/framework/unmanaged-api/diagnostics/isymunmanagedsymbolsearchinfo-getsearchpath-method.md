---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: 8477f53bec44675d7cb0a9bc6c4f11097a4fcc87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446160"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="f0ddc-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath, méthode</span><span class="sxs-lookup"><span data-stu-id="f0ddc-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="f0ddc-103">Obtient le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="f0ddc-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ddc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0ddc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ddc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0ddc-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="f0ddc-106">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="f0ddc-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0ddc-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f0ddc-107">Return Value</span></span>  
 <span data-ttu-id="f0ddc-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f0ddc-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ddc-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0ddc-109">Requirements</span></span>  
 <span data-ttu-id="f0ddc-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f0ddc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ddc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0ddc-111">See also</span></span>

- [<span data-ttu-id="f0ddc-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f0ddc-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
