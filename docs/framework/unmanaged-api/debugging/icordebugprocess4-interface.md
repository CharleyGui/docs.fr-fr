---
title: ICorDebugProcess4, interface
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213580"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="9f5a0-102">ICorDebugProcess4, interface</span><span class="sxs-lookup"><span data-stu-id="9f5a0-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="9f5a0-103">Prend en charge le contrôle de l’exécution hors processus.</span><span class="sxs-lookup"><span data-stu-id="9f5a0-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="9f5a0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9f5a0-104">Methods</span></span>

| <span data-ttu-id="9f5a0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9f5a0-105">Method</span></span>                                                                 | <span data-ttu-id="9f5a0-106">Description</span><span class="sxs-lookup"><span data-stu-id="9f5a0-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="9f5a0-107">Processstatechanged,</span><span class="sxs-lookup"><span data-stu-id="9f5a0-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="9f5a0-108">Notifie le pipeline ICorDebug que le débogueur hors processus poursuit l’exécution du débogueur.</span><span class="sxs-lookup"><span data-stu-id="9f5a0-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9f5a0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="9f5a0-109">Remarks</span></span>

<span data-ttu-id="9f5a0-110">Cette interface réside à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9f5a0-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="9f5a0-111">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `E930C679-78AF-4953-8AB7-B0AABF0F9F80` un GUID qui peut être obtenu par le biais des mécanismes com habituels.</span><span class="sxs-lookup"><span data-stu-id="9f5a0-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f5a0-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9f5a0-112">Requirements</span></span>

<span data-ttu-id="9f5a0-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f5a0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9f5a0-114">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="9f5a0-114">**Header:** None</span></span>

<span data-ttu-id="9f5a0-115">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="9f5a0-115">**Library:** None</span></span>

<span data-ttu-id="9f5a0-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f5a0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9f5a0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f5a0-117">See also</span></span>

- [<span data-ttu-id="9f5a0-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9f5a0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f5a0-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="9f5a0-119">Debugging</span></span>](index.md)
