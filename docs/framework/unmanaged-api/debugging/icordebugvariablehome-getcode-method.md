---
title: 'ICorDebugVariableHome :: GetCode, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: 87d611a7b6e12a9238b00131326e8205778769e6
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396589"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="7d624-102">ICorDebugVariableHome :: GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="7d624-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="7d624-103">Obtient l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d624-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d624-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d624-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d624-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d624-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7d624-106">à Pointeur vers l’adresse de l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d624-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d624-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7d624-107">Requirements</span></span>  
 <span data-ttu-id="7d624-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d624-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d624-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d624-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d624-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d624-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d624-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d624-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d624-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d624-112">See also</span></span>

- [<span data-ttu-id="7d624-113">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="7d624-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
