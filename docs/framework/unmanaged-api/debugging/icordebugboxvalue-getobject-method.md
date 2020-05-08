---
title: ICorDebugBoxValue::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: 401f052b881c1a0cfa065ba60c93aca1706f34f4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894784"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="a29a1-102">ICorDebugBoxValue::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="a29a1-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="a29a1-103">Obtient la valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="a29a1-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a29a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a29a1-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="a29a1-106">à Pointeur vers l’adresse d’un objet ICorDebugObjectValue qui représente la valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="a29a1-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29a1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a29a1-107">Requirements</span></span>  
 <span data-ttu-id="a29a1-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a29a1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29a1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a29a1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a29a1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a29a1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a29a1-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
