---
title: ISymUnmanagedMethod::GetOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 358f3d3d7c231a2baa9d2c467935ba3a5867e36b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614472"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="a1068-102">ISymUnmanagedMethod::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="a1068-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="a1068-103">Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="a1068-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1068-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1068-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1068-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a1068-106">dans Pointeur vers le document pour lequel l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="a1068-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="a1068-107">dans Ligne de document pour laquelle l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="a1068-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="a1068-108">dans Colonne de document pour laquelle l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="a1068-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a1068-109">à Pointeur vers un `ULONG32` qui reçoit les offsets.</span><span class="sxs-lookup"><span data-stu-id="a1068-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1068-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1068-110">Return Value</span></span>  
 <span data-ttu-id="a1068-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a1068-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1068-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a1068-112">Requirements</span></span>  
 <span data-ttu-id="a1068-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a1068-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1068-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1068-114">See also</span></span>

- [<span data-ttu-id="a1068-115">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="a1068-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
