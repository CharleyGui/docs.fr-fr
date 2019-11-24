---
title: ISymUnmanagedReader::GetMethodVersion, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: fcaf748413321f684336543e60f735af69894b51
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436011"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="3bdad-102">ISymUnmanagedReader::GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="3bdad-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="3bdad-103">Gets the method version.</span><span class="sxs-lookup"><span data-stu-id="3bdad-103">Gets the method version.</span></span> <span data-ttu-id="3bdad-104">The method version starts at 1 and is incremented each time the method is recompiled.</span><span class="sxs-lookup"><span data-stu-id="3bdad-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="3bdad-105">Recompilation can happen without changes to the method.</span><span class="sxs-lookup"><span data-stu-id="3bdad-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdad-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bdad-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bdad-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bdad-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="3bdad-108">[in] The method for which to get the version.</span><span class="sxs-lookup"><span data-stu-id="3bdad-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="3bdad-109">[out] A pointer to a variable that receives the method version.</span><span class="sxs-lookup"><span data-stu-id="3bdad-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bdad-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3bdad-110">Return Value</span></span>  
 <span data-ttu-id="3bdad-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="3bdad-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdad-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="3bdad-112">Requirements</span></span>  
 <span data-ttu-id="3bdad-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3bdad-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdad-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bdad-114">See also</span></span>

- [<span data-ttu-id="3bdad-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="3bdad-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
