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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62eb5782071b42df1a035a4553b6cf9da53e24ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778101"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="3ff42-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath, méthode</span><span class="sxs-lookup"><span data-stu-id="3ff42-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="3ff42-103">Obtient le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="3ff42-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ff42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ff42-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3ff42-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="3ff42-106">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="3ff42-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ff42-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3ff42-107">Return Value</span></span>  
 <span data-ttu-id="3ff42-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3ff42-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff42-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3ff42-109">Requirements</span></span>  
 <span data-ttu-id="3ff42-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3ff42-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff42-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ff42-111">See also</span></span>

- [<span data-ttu-id="3ff42-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="3ff42-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
