---
title: ISymUnmanagedReader::GetMethodByVersion, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: d5f42e5ed3ce7829cfcf921f3002c238985710a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426747"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="2cc88-102">ISymUnmanagedReader::GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2cc88-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="2cc88-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span><span class="sxs-lookup"><span data-stu-id="2cc88-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="2cc88-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span><span class="sxs-lookup"><span data-stu-id="2cc88-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc88-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc88-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cc88-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2cc88-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="2cc88-107">[in] The method token.</span><span class="sxs-lookup"><span data-stu-id="2cc88-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="2cc88-108">[in] The method version.</span><span class="sxs-lookup"><span data-stu-id="2cc88-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2cc88-109">[out] A pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="2cc88-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cc88-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2cc88-110">Return Value</span></span>  
 <span data-ttu-id="2cc88-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="2cc88-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cc88-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="2cc88-112">Requirements</span></span>  
 <span data-ttu-id="2cc88-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2cc88-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc88-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cc88-114">See also</span></span>

- [<span data-ttu-id="2cc88-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="2cc88-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
