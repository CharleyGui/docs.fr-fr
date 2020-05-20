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
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615317"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="3da90-102">ISymUnmanagedSourceServerModule::GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="3da90-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="3da90-103">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="3da90-103">Returns the source server data for the module.</span></span> <span data-ttu-id="3da90-104">L’appelant doit libérer des ressources à l’aide de `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="3da90-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da90-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3da90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3da90-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3da90-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="3da90-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en octets, des données du serveur source.</span><span class="sxs-lookup"><span data-stu-id="3da90-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="3da90-108">à Pointeur vers la valeur retournée `pDataByteCount` .</span><span class="sxs-lookup"><span data-stu-id="3da90-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3da90-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3da90-109">Return Value</span></span>  
 <span data-ttu-id="3da90-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3da90-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da90-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3da90-111">Requirements</span></span>  
 <span data-ttu-id="3da90-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3da90-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da90-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3da90-113">See also</span></span>

- [<span data-ttu-id="3da90-114">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="3da90-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
