---
title: ICorDebugModule::GetClassFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
ms.openlocfilehash: 790999093f874a4d81dd5db74ef012b1d997a12f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109648"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="a35ef-102">ICorDebugModule::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="a35ef-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="a35ef-103">Obtient la classe spécifiée par le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a35ef-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a35ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a35ef-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="a35ef-106">dans `mdTypeDef` jeton de métadonnées qui référence les métadonnées d’une classe.</span><span class="sxs-lookup"><span data-stu-id="a35ef-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="a35ef-107">à Pointeur vers l’adresse d’un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="a35ef-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35ef-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="a35ef-108">Requirements</span></span>  
 <span data-ttu-id="a35ef-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35ef-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35ef-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a35ef-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a35ef-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a35ef-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a35ef-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35ef-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
