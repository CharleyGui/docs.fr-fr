---
title: ICorDebugType::GetBase, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: fc406f6e87e5b2be48c6fe7d5fc988774ac5cd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379983"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="d87ce-102">ICorDebugType::GetBase, méthode</span><span class="sxs-lookup"><span data-stu-id="d87ce-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="d87ce-103">Obtient un pointeur d’interface vers un ICorDebugType qui représente le type de base, le cas échéant, du type représenté par ce `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="d87ce-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d87ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d87ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d87ce-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="d87ce-106">à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le type de base.</span><span class="sxs-lookup"><span data-stu-id="d87ce-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d87ce-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="d87ce-107">Remarks</span></span>  
 <span data-ttu-id="d87ce-108">La recherche du type de base pour un type est utile pour implémenter les fonctionnalités de débogueur courantes, telles que l’impression de tous les champs d’un objet ou de ses classes parentes.</span><span class="sxs-lookup"><span data-stu-id="d87ce-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d87ce-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d87ce-109">Requirements</span></span>  
 <span data-ttu-id="d87ce-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d87ce-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d87ce-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d87ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d87ce-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d87ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d87ce-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d87ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
