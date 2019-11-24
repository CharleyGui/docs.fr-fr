---
title: ISymUnmanagedSourceServerModule::GetSourceServerData, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: f25150d037a2f6fabb700f2c4bf2191e8e402a8e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446208"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="ee62e-102">ISymUnmanagedSourceServerModule::GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="ee62e-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="ee62e-103">Returns the source server data for the module.</span><span class="sxs-lookup"><span data-stu-id="ee62e-103">Returns the source server data for the module.</span></span> <span data-ttu-id="ee62e-104">The caller must free resources by using `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="ee62e-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee62e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee62e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee62e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee62e-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="ee62e-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span><span class="sxs-lookup"><span data-stu-id="ee62e-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="ee62e-108">[out] A pointer to the returned `pDataByteCount` value.</span><span class="sxs-lookup"><span data-stu-id="ee62e-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee62e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ee62e-109">Return Value</span></span>  
 <span data-ttu-id="ee62e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="ee62e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee62e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="ee62e-111">Requirements</span></span>  
 <span data-ttu-id="ee62e-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ee62e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee62e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee62e-113">See also</span></span>

- [<span data-ttu-id="ee62e-114">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="ee62e-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
