---
title: ICorDebugModule::GetFunctionFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: bf2acd897c9c45e445b864f85550ed7ed6e00886
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710153"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="d6367-102">ICorDebugModule::GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d6367-102">ICorDebugModule::GetFunctionFromToken Method</span></span>

<span data-ttu-id="d6367-103">Obtient la fonction spécifiée par le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d6367-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6367-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6367-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6367-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6367-105">Parameters</span></span>  

 `methodDef`  
 <span data-ttu-id="d6367-106">dans `mdMethodDef` Jeton de métadonnées qui fait référence aux métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d6367-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="d6367-107">à Pointeur vers l’adresse d’un objet d’interface ICorDebugFunction qui représente la fonction.</span><span class="sxs-lookup"><span data-stu-id="d6367-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6367-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d6367-108">Remarks</span></span>  

 <span data-ttu-id="d6367-109">La `GetFunctionFromToken` méthode retourne un CORDBG_E_FUNCTION_NOT_IL HRESULT si la valeur passée `methodDef` ne fait pas référence à une méthode MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d6367-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6367-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6367-110">Requirements</span></span>  

 <span data-ttu-id="d6367-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6367-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6367-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6367-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6367-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6367-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6367-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6367-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
