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
ms.openlocfilehash: 7e32f3f4f6613d34e2b40946ed3eadb8eb0a7c1f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212566"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="b8456-102">ICorDebugModule::GetGlobalVariableValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b8456-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="b8456-103">Obtient la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b8456-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8456-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8456-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8456-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8456-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="b8456-106">dans `mdFieldDef`Jeton qui fait référence aux métadonnées décrivant la variable globale.</span><span class="sxs-lookup"><span data-stu-id="b8456-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b8456-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b8456-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8456-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8456-108">Requirements</span></span>  
 <span data-ttu-id="b8456-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8456-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8456-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8456-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8456-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8456-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8456-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8456-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
