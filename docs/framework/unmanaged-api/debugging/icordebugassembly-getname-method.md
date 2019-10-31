---
title: ICorDebugAssembly::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127171"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="bcae1-102">ICorDebugAssembly::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="bcae1-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="bcae1-103">Obtient le nom de l’assembly que cette `ICorDebugAssembly` instance représente.</span><span class="sxs-lookup"><span data-stu-id="bcae1-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcae1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcae1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcae1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcae1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="bcae1-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="bcae1-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bcae1-107">à Pointeur vers un entier qui spécifie la longueur réelle du nom.</span><span class="sxs-lookup"><span data-stu-id="bcae1-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="bcae1-108">à Tableau qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="bcae1-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcae1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bcae1-109">Remarks</span></span>  
 <span data-ttu-id="bcae1-110">La méthode `GetName` retourne le chemin d’accès complet et le nom de fichier de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcae1-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcae1-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="bcae1-111">Requirements</span></span>  
 <span data-ttu-id="bcae1-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcae1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcae1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcae1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcae1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcae1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcae1-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcae1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
