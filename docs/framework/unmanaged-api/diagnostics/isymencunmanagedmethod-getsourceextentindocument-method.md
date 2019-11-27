---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: b8e72745eff09c6707afe5a5f20a1ddf38b239ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448621"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="2a004-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="2a004-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="2a004-103">Obtient la ligne de début la plus petite et la ligne de fin la plus grande pour la méthode dans un document spécifique.</span><span class="sxs-lookup"><span data-stu-id="2a004-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a004-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a004-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a004-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a004-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="2a004-106">dans Pointeur vers le document.</span><span class="sxs-lookup"><span data-stu-id="2a004-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="2a004-107">à Pointeur vers un `ULONG32` qui reçoit la ligne de début.</span><span class="sxs-lookup"><span data-stu-id="2a004-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="2a004-108">à Pointeur vers un `ULONG32` qui reçoit la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="2a004-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a004-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2a004-109">Return Value</span></span>  
 <span data-ttu-id="2a004-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2a004-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a004-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a004-111">Requirements</span></span>  
 <span data-ttu-id="2a004-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2a004-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a004-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a004-113">See also</span></span>

- [<span data-ttu-id="2a004-114">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="2a004-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
