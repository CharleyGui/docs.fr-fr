---
title: ICorDebugAppDomain2::GetFunctionPointerType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: be797b1b3f288fd367d7f624e9cf33015dd114ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698271"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="559a2-102">ICorDebugAppDomain2::GetFunctionPointerType, méthode</span><span class="sxs-lookup"><span data-stu-id="559a2-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="559a2-103">Obtient un pointeur vers une fonction qui a une signature donnée.</span><span class="sxs-lookup"><span data-stu-id="559a2-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="559a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="559a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="559a2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="559a2-105">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="559a2-106">dans Nombre d’arguments de type pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="559a2-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="559a2-107">dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="559a2-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="559a2-108">Le premier élément est le type de retour ; chacun des autres éléments est un type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="559a2-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="559a2-109">à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le pointeur vers la fonction.</span><span class="sxs-lookup"><span data-stu-id="559a2-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="559a2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="559a2-110">Requirements</span></span>  

 <span data-ttu-id="559a2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="559a2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="559a2-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="559a2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="559a2-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="559a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="559a2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="559a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
