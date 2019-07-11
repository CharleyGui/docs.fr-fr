---
title: ISOSDacInterface::GetMethodDescPtrFromIP (méthode)
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
ms.openlocfilehash: cd256250021436e611142de11c3625a21aeec814
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764745"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="b4362-102">ISOSDacInterface::GetMethodDescPtrFromIP (méthode)</span><span class="sxs-lookup"><span data-stu-id="b4362-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="b4362-103">Récupère le pointeur de la MethodDesc correspondant de la méthode contenant l’adresse d’instruction natif donné.</span><span class="sxs-lookup"><span data-stu-id="b4362-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4362-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4362-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="b4362-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4362-105">Parameters</span></span>

`ip`\
<span data-ttu-id="b4362-106">[in] Une adresse dans la méthode lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b4362-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="b4362-107">[out] L’adresse de le `MethodDesc` pour la méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="b4362-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4362-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b4362-108">Remarks</span></span>

<span data-ttu-id="b4362-109">La méthode fournie fait partie de la [ `ISOSDacInterface` interface](isosdacinterface-interface.md) et correspond à l’emplacement de la table de la méthode virtuelle de 21.</span><span class="sxs-lookup"><span data-stu-id="b4362-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4362-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4362-110">Requirements</span></span>

<span data-ttu-id="b4362-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4362-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4362-112">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="b4362-112">**Header:** None</span></span>  
<span data-ttu-id="b4362-113">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="b4362-113">**Library:** None</span></span>  
<span data-ttu-id="b4362-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4362-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4362-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4362-115">See also</span></span>

- [<span data-ttu-id="b4362-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="b4362-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4362-117">Interface de ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="b4362-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
