---
title: ICorDebugThread::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: 2c13ead228296525b57245be8b3bdbcdf38ae173
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728002"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="04548-102">ICorDebugThread::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="04548-102">ICorDebugThread::GetObject Method</span></span>

<span data-ttu-id="04548-103">Obtient un pointeur d’interface vers le thread common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="04548-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04548-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04548-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04548-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04548-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="04548-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le thread CLR.</span><span class="sxs-lookup"><span data-stu-id="04548-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04548-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="04548-107">Requirements</span></span>  

 <span data-ttu-id="04548-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04548-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04548-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04548-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04548-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04548-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04548-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04548-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04548-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04548-112">See also</span></span>

- <xref:System.Threading.Thread>
