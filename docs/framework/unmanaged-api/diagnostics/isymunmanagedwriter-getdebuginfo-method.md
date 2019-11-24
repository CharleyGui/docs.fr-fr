---
title: ISymUnmanagedWriter::GetDebugInfo, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: 2b901a3dac499f1ce3f843c59122dd8fd5022147
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427964"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="86ab2-102">ISymUnmanagedWriter::GetDebugInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="86ab2-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="86ab2-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span><span class="sxs-lookup"><span data-stu-id="86ab2-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="86ab2-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="86ab2-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="86ab2-105">(The compiler is responsible for setting these two fields appropriately.)</span><span class="sxs-lookup"><span data-stu-id="86ab2-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="86ab2-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span><span class="sxs-lookup"><span data-stu-id="86ab2-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="86ab2-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span><span class="sxs-lookup"><span data-stu-id="86ab2-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ab2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86ab2-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86ab2-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86ab2-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="86ab2-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span><span class="sxs-lookup"><span data-stu-id="86ab2-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="86ab2-111">[in] A `DWORD` that contains the size of the debug data.</span><span class="sxs-lookup"><span data-stu-id="86ab2-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="86ab2-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span><span class="sxs-lookup"><span data-stu-id="86ab2-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="86ab2-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span><span class="sxs-lookup"><span data-stu-id="86ab2-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86ab2-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="86ab2-114">Return Value</span></span>  
 <span data-ttu-id="86ab2-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="86ab2-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86ab2-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="86ab2-116">Requirements</span></span>  
 <span data-ttu-id="86ab2-117">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="86ab2-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ab2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86ab2-118">See also</span></span>

- [<span data-ttu-id="86ab2-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="86ab2-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
