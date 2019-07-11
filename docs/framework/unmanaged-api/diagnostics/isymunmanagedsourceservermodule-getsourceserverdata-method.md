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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22321dc8f8c4b8d9c2ae50b061a2ba105f92ebb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746085"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="d208f-102">ISymUnmanagedSourceServerModule::GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="d208f-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="d208f-103">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="d208f-103">Returns the source server data for the module.</span></span> <span data-ttu-id="d208f-104">L’appelant doit libérer des ressources à l’aide de `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="d208f-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d208f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d208f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d208f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d208f-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="d208f-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en octets, des données de serveur source.</span><span class="sxs-lookup"><span data-stu-id="d208f-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="d208f-108">[out] Un pointeur vers le texte retourné `pDataByteCount` valeur.</span><span class="sxs-lookup"><span data-stu-id="d208f-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d208f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d208f-109">Return Value</span></span>  
 <span data-ttu-id="d208f-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d208f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d208f-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d208f-111">Requirements</span></span>  
 <span data-ttu-id="d208f-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d208f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d208f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d208f-113">See also</span></span>

- [<span data-ttu-id="d208f-114">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="d208f-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
