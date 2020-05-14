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
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396928"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="27efc-102">ISOSDacInterface :: GetMethodDescPtrFromIP, méthode</span><span class="sxs-lookup"><span data-stu-id="27efc-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="27efc-103">Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée.</span><span class="sxs-lookup"><span data-stu-id="27efc-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="27efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27efc-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="27efc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27efc-105">Parameters</span></span>

`ip`\
<span data-ttu-id="27efc-106">dans Adresse dans la méthode au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="27efc-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="27efc-107">à Adresse du `MethodDesc` pour la méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="27efc-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="27efc-108">Notes</span><span class="sxs-lookup"><span data-stu-id="27efc-108">Remarks</span></span>

<span data-ttu-id="27efc-109">La méthode fournie fait partie de l' [ `ISOSDacInterface` interface](isosdacinterface-interface.md) et correspond à l’emplacement 22 de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="27efc-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="27efc-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27efc-110">Requirements</span></span>

<span data-ttu-id="27efc-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27efc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="27efc-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="27efc-112">**Header:** None</span></span>  
<span data-ttu-id="27efc-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="27efc-113">**Library:** None</span></span>  
<span data-ttu-id="27efc-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27efc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="27efc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27efc-115">See also</span></span>

- [<span data-ttu-id="27efc-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="27efc-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="27efc-117">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="27efc-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
