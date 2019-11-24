---
title: ISymUnmanagedMethod::GetSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448879"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="f8e3a-102">ISymUnmanagedMethod::GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="f8e3a-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="f8e3a-103">Gets all the sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8e3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8e3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8e3a-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="f8e3a-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="f8e3a-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="f8e3a-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="f8e3a-109">[in] An array in which to store the documents in which the sequence points are located.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="f8e3a-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="f8e3a-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="f8e3a-112">[in] The array of lines in the documents at which the sequence points end.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="f8e3a-113">[in] The array of columns in the documents at which the sequence points end.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8e3a-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8e3a-114">Return Value</span></span>  
 <span data-ttu-id="f8e3a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="f8e3a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8e3a-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="f8e3a-116">Requirements</span></span>  
 <span data-ttu-id="f8e3a-117">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8e3a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e3a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8e3a-118">See also</span></span>

- [<span data-ttu-id="f8e3a-119">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="f8e3a-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
