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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893653"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="8e6d4-102">ICorDebugCode::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="8e6d4-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="8e6d4-103">Obtient tout le code pour la fonction spécifiée, mis en forme pour le code machine.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="8e6d4-104">Cette méthode est déconseillée dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8e6d4-105">Utilisez [ICorDebugCode2 :: GetCodeChunks,](icordebugcode2-getcodechunks-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e6d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e6d4-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8e6d4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e6d4-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="8e6d4-108">dans Offset du début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="8e6d4-109">dans Offset de la fin de la fonction.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="8e6d4-110">dans Taille du `buffer` tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8e6d4-111">à Tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="8e6d4-112">à Nombre d’octets retournés.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e6d4-113">Notes </span><span class="sxs-lookup"><span data-stu-id="8e6d4-113">Remarks</span></span>  
 <span data-ttu-id="8e6d4-114">Si le code de la fonction a été divisé en plusieurs segments, ils sont concaténés par ordre de décalage natif.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="8e6d4-115">Les limites d’instruction ne sont pas vérifiées.</span><span class="sxs-lookup"><span data-stu-id="8e6d4-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e6d4-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8e6d4-116">Requirements</span></span>  
 <span data-ttu-id="8e6d4-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e6d4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e6d4-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e6d4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e6d4-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e6d4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e6d4-120">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="8e6d4-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6d4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e6d4-121">See also</span></span>

- [<span data-ttu-id="8e6d4-122">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="8e6d4-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
