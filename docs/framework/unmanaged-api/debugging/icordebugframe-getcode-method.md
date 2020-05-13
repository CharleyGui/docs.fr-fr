---
title: ICorDebugFrame::GetCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: c8914ba1090ec5fd6540e9ead302675cb44f37e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208601"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="148b6-102">ICorDebugFrame::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="148b6-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="148b6-103">Obtient un pointeur vers le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="148b6-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="148b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="148b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="148b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="148b6-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="148b6-106">à Pointeur vers l’adresse d’un objet ICorDebugCode qui représente le code associé à ce frame.</span><span class="sxs-lookup"><span data-stu-id="148b6-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="148b6-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="148b6-107">Requirements</span></span>  
 <span data-ttu-id="148b6-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148b6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148b6-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="148b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="148b6-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="148b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="148b6-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="148b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
