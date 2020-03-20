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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176576"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="91422-102">ISymUnmanagedSourceServerModule::GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="91422-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="91422-103">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="91422-103">Returns the source server data for the module.</span></span> <span data-ttu-id="91422-104">L’appelant doit libérer `CoTaskMemFree`des ressources en utilisant .</span><span class="sxs-lookup"><span data-stu-id="91422-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91422-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91422-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91422-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91422-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="91422-107">[out] Un pointeur `ULONG32` à un qui reçoit la taille, dans les octets, des données du serveur source.</span><span class="sxs-lookup"><span data-stu-id="91422-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="91422-108">[out] Un pointeur `pDataByteCount` à la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="91422-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91422-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="91422-109">Return Value</span></span>  
 <span data-ttu-id="91422-110">S_OK si la méthode réussit; autrement, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="91422-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91422-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="91422-111">Requirements</span></span>  
 <span data-ttu-id="91422-112">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="91422-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91422-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91422-113">See also</span></span>

- [<span data-ttu-id="91422-114">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="91422-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
