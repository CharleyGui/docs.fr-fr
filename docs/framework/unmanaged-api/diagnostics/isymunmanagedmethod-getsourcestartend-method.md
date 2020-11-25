---
title: ISymUnmanagedMethod::GetSourceStartEnd, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: f53afa5f87f1502f287b25e3d9756f9a54ad6869
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699285"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="c3578-102">ISymUnmanagedMethod::GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="c3578-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>

<span data-ttu-id="c3578-103">Obtient les positions de début et de fin du document pour la source de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c3578-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="c3578-104">La première position de tableau est le début, tandis que la deuxième position de tableau est la fin.</span><span class="sxs-lookup"><span data-stu-id="c3578-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3578-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3578-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3578-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3578-106">Parameters</span></span>  

 `docs`  
 <span data-ttu-id="c3578-107">dans Documents source de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="c3578-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="c3578-108">dans Lignes de début et de fin dans les documents sources correspondants.</span><span class="sxs-lookup"><span data-stu-id="c3578-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="c3578-109">dans Colonnes de début et de fin dans les documents sources correspondants.</span><span class="sxs-lookup"><span data-stu-id="c3578-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c3578-110">[out] `true` Si les positions ont été définies ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="c3578-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3578-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c3578-111">Return Value</span></span>  

 <span data-ttu-id="c3578-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c3578-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3578-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3578-113">Requirements</span></span>  

 <span data-ttu-id="c3578-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c3578-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3578-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3578-115">See also</span></span>

- [<span data-ttu-id="c3578-116">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="c3578-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
