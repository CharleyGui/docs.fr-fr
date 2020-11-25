---
title: ISymENCUnmanagedMethod::GetLineFromOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707358"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="a35f6-102">ISymENCUnmanagedMethod::GetLineFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="a35f6-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="a35f6-103">Obtient les informations de ligne associées à un offset.</span><span class="sxs-lookup"><span data-stu-id="a35f6-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="a35f6-104">Si le paramètre de décalage ( `dwOffset` ) n’est pas un point de séquence, cette méthode obtient les informations de ligne associées au décalage précédent.</span><span class="sxs-lookup"><span data-stu-id="a35f6-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a35f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35f6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a35f6-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="a35f6-107">dans `ULONG32` Qui contient l’offset.</span><span class="sxs-lookup"><span data-stu-id="a35f6-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="a35f6-108">à Pointeur vers un `ULONG32` qui reçoit la ligne.</span><span class="sxs-lookup"><span data-stu-id="a35f6-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="a35f6-109">à Pointeur vers un `ULONG32` qui reçoit la colonne.</span><span class="sxs-lookup"><span data-stu-id="a35f6-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="a35f6-110">à Pointeur vers un `ULONG32` qui reçoit la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="a35f6-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="a35f6-111">à Pointeur vers un `ULONG32` qui reçoit la colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="a35f6-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="a35f6-112">à Pointeur vers un `ULONG32` qui reçoit le point de séquence associé.</span><span class="sxs-lookup"><span data-stu-id="a35f6-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a35f6-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a35f6-113">Return Value</span></span>  

 <span data-ttu-id="a35f6-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a35f6-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35f6-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a35f6-115">Requirements</span></span>  

 <span data-ttu-id="a35f6-116">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a35f6-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35f6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a35f6-117">See also</span></span>

- [<span data-ttu-id="a35f6-118">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="a35f6-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
