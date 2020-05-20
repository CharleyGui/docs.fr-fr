---
title: 'ISOSDacInterface :: GetMethodDescPtrFromIP, méthode'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421005"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="5f293-102">ISOSDacInterface :: GetMethodDescPtrFromIP, méthode</span><span class="sxs-lookup"><span data-stu-id="5f293-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="5f293-103">Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée.</span><span class="sxs-lookup"><span data-stu-id="5f293-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5f293-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f293-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="5f293-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5f293-105">Parameters</span></span>

`ip`\
<span data-ttu-id="5f293-106">dans Adresse dans la méthode au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5f293-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="5f293-107">à Adresse du `MethodDesc` pour la méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="5f293-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f293-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5f293-108">Remarks</span></span>

<span data-ttu-id="5f293-109">La méthode fournie fait partie de l' [ `ISOSDacInterface` interface](isosdacinterface-interface.md) et correspond à l’emplacement 22 de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="5f293-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f293-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="5f293-110">Requirements</span></span>

<span data-ttu-id="5f293-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f293-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5f293-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="5f293-112">**Header:** None</span></span>  
<span data-ttu-id="5f293-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="5f293-113">**Library:** None</span></span>  
<span data-ttu-id="5f293-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f293-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5f293-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f293-115">See also</span></span>

- [<span data-ttu-id="5f293-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="5f293-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="5f293-117">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="5f293-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
