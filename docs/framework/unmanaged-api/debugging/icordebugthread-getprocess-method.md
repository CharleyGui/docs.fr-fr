---
title: ICorDebugThread::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 76dfc10b9d9069f6d53cd292f241ae3080c6443a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379807"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="35130-102">ICorDebugThread::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="35130-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="35130-103">Obtient un pointeur d’interface vers le processus dont ce ICorDebugThread forme un composant.</span><span class="sxs-lookup"><span data-stu-id="35130-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35130-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35130-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35130-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="35130-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="35130-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35130-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35130-107">Requirements</span></span>  
 <span data-ttu-id="35130-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35130-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35130-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35130-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35130-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35130-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35130-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35130-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
