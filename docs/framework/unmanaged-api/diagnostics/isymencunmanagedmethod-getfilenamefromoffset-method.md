---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 74002ce9c76eebaa3ea5860b09cd3e7c9a884f8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448654"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="d995c-102">ISymENCUnmanagedMethod::GetFileNameFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="d995c-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="d995c-103">Obtient le nom de fichier pour la ligne associée à un offset.</span><span class="sxs-lookup"><span data-stu-id="d995c-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d995c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d995c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d995c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d995c-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="d995c-106">dans `ULONG32` qui contient le décalage.</span><span class="sxs-lookup"><span data-stu-id="d995c-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d995c-107">dans `ULONG32` qui indique la taille de la mémoire tampon de `szName`.</span><span class="sxs-lookup"><span data-stu-id="d995c-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d995c-108">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon qui doit contenir les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d995c-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="d995c-109">à Mémoire tampon qui contient les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d995c-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d995c-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d995c-110">Return Value</span></span>  
 <span data-ttu-id="d995c-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d995c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d995c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d995c-112">Requirements</span></span>  
 <span data-ttu-id="d995c-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d995c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d995c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d995c-114">See also</span></span>

- [<span data-ttu-id="d995c-115">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="d995c-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
