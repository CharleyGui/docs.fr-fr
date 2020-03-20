---
title: ICorDebugCode::GetCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179000"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="dba8d-102">ICorDebugCode::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="dba8d-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="dba8d-103">Obtient tout le code pour la fonction spécifiée, formaté pour démontage.</span><span class="sxs-lookup"><span data-stu-id="dba8d-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="dba8d-104">Cette méthode a été dépréciée dans la version cadre .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="dba8d-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="dba8d-105">Utilisez [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="dba8d-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba8d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dba8d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba8d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dba8d-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="dba8d-108">[dans] Le décalage du début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dba8d-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="dba8d-109">[dans] Le décalage de la fin de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dba8d-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="dba8d-110">[dans] La taille `buffer` du tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="dba8d-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="dba8d-111">[out] Le tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="dba8d-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="dba8d-112">[out] Le nombre d’octets est revenu.</span><span class="sxs-lookup"><span data-stu-id="dba8d-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba8d-113">Notes </span><span class="sxs-lookup"><span data-stu-id="dba8d-113">Remarks</span></span>  
 <span data-ttu-id="dba8d-114">Si le code de la fonction a été divisé en plusieurs morceaux, ils sont concatenated dans l’ordre d’augmenter la compensation indigène.</span><span class="sxs-lookup"><span data-stu-id="dba8d-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="dba8d-115">Les limites de l’instruction ne sont pas vérifiées.</span><span class="sxs-lookup"><span data-stu-id="dba8d-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba8d-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dba8d-116">Requirements</span></span>  
 <span data-ttu-id="dba8d-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba8d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba8d-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba8d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba8d-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba8d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba8d-120">**Versions cadre .NET:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="dba8d-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba8d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dba8d-121">See also</span></span>

- [<span data-ttu-id="dba8d-122">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="dba8d-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
