---
title: ICorDebugAssembly::GetCodeBase, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetCodeBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetCodeBase
helpviewer_keywords:
- GetCodeBase method [.NET Framework debugging]
- ICorDebugAssembly::GetCodeBase method [.NET Framework debugging]
ms.assetid: 48adc154-9058-4fef-9c43-e9aad80e4dbf
topic_type:
- apiref
ms.openlocfilehash: 92e07d2f59a1f2fa063b81282aa0f014f373cd04
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196361"
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="440f3-102">ICorDebugAssembly::GetCodeBase, méthode</span><span class="sxs-lookup"><span data-stu-id="440f3-102">ICorDebugAssembly::GetCodeBase Method</span></span>
<span data-ttu-id="440f3-103">Cette méthode n’est pas implémentée dans la version actuelle du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="440f3-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="440f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="440f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR szName[]  
);  
```
