---
title: ICorDebugThread::GetRegisterSet, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: 7d3575909f54c8d676c9fd4246e6eac4a8a0ea1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727976"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="c14b8-102">ICorDebugThread::GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="c14b8-102">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="c14b8-103">Obtient un pointeur d’interface vers le jeu de registres associé à la partie active de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c14b8-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c14b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c14b8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c14b8-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="c14b8-106">à Pointeur vers l’adresse d’un objet d’interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) qui représente le jeu de registres pour la partie active de ce thread.</span><span class="sxs-lookup"><span data-stu-id="c14b8-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c14b8-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c14b8-107">Requirements</span></span>  

 <span data-ttu-id="c14b8-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14b8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c14b8-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c14b8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c14b8-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c14b8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c14b8-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c14b8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
