---
title: ICorDebugProcess5::GetTypeForTypeID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212761"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="16bb4-102">ICorDebugProcess5::GetTypeForTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="16bb4-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="16bb4-103">Convertit un identificateur de type en valeur ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="16bb4-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16bb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16bb4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16bb4-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="16bb4-106">dans Identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="16bb4-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="16bb4-107">à Pointeur vers l’adresse d’un objet ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="16bb4-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16bb4-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="16bb4-108">Remarks</span></span>  
 <span data-ttu-id="16bb4-109">Dans certains cas, les méthodes qui retournent un identificateur de type peuvent retourner une `COR_TYPEID` valeur null.</span><span class="sxs-lookup"><span data-stu-id="16bb4-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="16bb4-110">Si cette valeur est passée comme `id` argument, la `GetTypeForTypeID` méthode échoue et retourne `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="16bb4-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bb4-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="16bb4-111">Requirements</span></span>  
 <span data-ttu-id="16bb4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16bb4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16bb4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16bb4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16bb4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16bb4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16bb4-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16bb4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bb4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16bb4-116">See also</span></span>

- [<span data-ttu-id="16bb4-117">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="16bb4-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="16bb4-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="16bb4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
