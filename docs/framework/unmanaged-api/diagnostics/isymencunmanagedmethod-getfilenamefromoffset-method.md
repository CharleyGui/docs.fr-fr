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
ms.openlocfilehash: ad9631039c8d032e7ffdba1e6098b66398f82277
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707384"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="1d829-102">ISymENCUnmanagedMethod::GetFileNameFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="1d829-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>

<span data-ttu-id="1d829-103">Obtient le nom de fichier pour la ligne associée à un offset.</span><span class="sxs-lookup"><span data-stu-id="1d829-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d829-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d829-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d829-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d829-105">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="1d829-106">dans `ULONG32` Qui contient l’offset.</span><span class="sxs-lookup"><span data-stu-id="1d829-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1d829-107">dans `ULONG32` Qui indique la taille de la `szName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1d829-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1d829-108">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon qui doit contenir les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1d829-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d829-109">à Mémoire tampon qui contient les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1d829-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d829-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1d829-110">Return Value</span></span>  

 <span data-ttu-id="1d829-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1d829-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d829-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d829-112">Requirements</span></span>  

 <span data-ttu-id="1d829-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1d829-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d829-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d829-114">See also</span></span>

- [<span data-ttu-id="1d829-115">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="1d829-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
