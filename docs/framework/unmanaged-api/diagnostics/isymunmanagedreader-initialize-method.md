---
title: ISymUnmanagedReader::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429736"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="b301b-102">ISymUnmanagedReader::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="b301b-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="b301b-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span><span class="sxs-lookup"><span data-stu-id="b301b-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b301b-104">This method can be called only once, and must be called before any other reader methods.</span><span class="sxs-lookup"><span data-stu-id="b301b-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b301b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b301b-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b301b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b301b-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="b301b-107">[in] The metadata importer interface with which this reader will be associated.</span><span class="sxs-lookup"><span data-stu-id="b301b-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="b301b-108">[in] The file name of the module.</span><span class="sxs-lookup"><span data-stu-id="b301b-108">[in] The file name of the module.</span></span> <span data-ttu-id="b301b-109">You can use the `pIStream` parameter instead.</span><span class="sxs-lookup"><span data-stu-id="b301b-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b301b-110">[in] The path to search.</span><span class="sxs-lookup"><span data-stu-id="b301b-110">[in] The path to search.</span></span> <span data-ttu-id="b301b-111">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="b301b-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="b301b-112">[in] The file stream, used as an alternative to the filename parameter.</span><span class="sxs-lookup"><span data-stu-id="b301b-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b301b-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b301b-113">Return Value</span></span>  
 <span data-ttu-id="b301b-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="b301b-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b301b-115">Notes</span><span class="sxs-lookup"><span data-stu-id="b301b-115">Remarks</span></span>  
 <span data-ttu-id="b301b-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span><span class="sxs-lookup"><span data-stu-id="b301b-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="b301b-117">Le paramètre `searchPath` est optionnel.</span><span class="sxs-lookup"><span data-stu-id="b301b-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b301b-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="b301b-118">Requirements</span></span>  
 <span data-ttu-id="b301b-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b301b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b301b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b301b-120">See also</span></span>

- [<span data-ttu-id="b301b-121">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="b301b-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
