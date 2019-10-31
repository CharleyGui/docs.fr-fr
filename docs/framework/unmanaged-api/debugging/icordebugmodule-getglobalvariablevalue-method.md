---
title: ICorDebugModule::GetGlobalVariableValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: 3afefdc3d704044184ea20d061eb9449458b5060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129578"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="a057a-102">ICorDebugModule::GetGlobalVariableValue, méthode</span><span class="sxs-lookup"><span data-stu-id="a057a-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="a057a-103">Obtient la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a057a-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a057a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a057a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a057a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a057a-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="a057a-106">dans Jeton `mdFieldDef` qui référence les métadonnées décrivant la variable globale.</span><span class="sxs-lookup"><span data-stu-id="a057a-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a057a-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a057a-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a057a-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="a057a-108">Requirements</span></span>  
 <span data-ttu-id="a057a-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a057a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a057a-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a057a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a057a-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a057a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a057a-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a057a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
