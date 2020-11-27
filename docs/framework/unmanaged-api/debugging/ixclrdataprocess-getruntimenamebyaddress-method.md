---
title: 'IXCLRDataProcess :: GetRuntimeNameByAddress, méthode'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270489"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="5721d-102">IXCLRDataProcess :: GetRuntimeNameByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="5721d-102">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="5721d-103">Obtient un nom pour l’adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="5721d-103">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5721d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5721d-104">Syntax</span></span>

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a><span data-ttu-id="5721d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5721d-105">Parameters</span></span>

`address`\
<span data-ttu-id="5721d-106">dans `CLRDATA_ADDRESS` Valeur qui représente une adresse de code.</span><span class="sxs-lookup"><span data-stu-id="5721d-106">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="5721d-107">dans Défini sur « 0 ».</span><span class="sxs-lookup"><span data-stu-id="5721d-107">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="5721d-108">dans Longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5721d-108">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="5721d-109">à Pointeur vers le nombre de caractères retournés.</span><span class="sxs-lookup"><span data-stu-id="5721d-109">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="5721d-110">[out, size_is ( `bufLen` )] mémoire tampon d’entrée de longueur `bufLen` qui stocke le nom du Runtime.</span><span class="sxs-lookup"><span data-stu-id="5721d-110">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="5721d-111">à `CLRDATA_ADDRESS` Pointeur vers l’offset de code du symbole retourné.</span><span class="sxs-lookup"><span data-stu-id="5721d-111">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="5721d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="5721d-112">Remarks</span></span>

<span data-ttu-id="5721d-113">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 16ème emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="5721d-113">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="5721d-114">Si la mémoire tampon n’est pas assez grande pour le nom, cette méthode retourne `S_FALSE` et définit `nameLen` la longueur de mémoire tampon requise.</span><span class="sxs-lookup"><span data-stu-id="5721d-114">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="5721d-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5721d-115">Requirements</span></span>

<span data-ttu-id="5721d-116">**Plateformes :** Voir [Configuration système requise](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="5721d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="5721d-117">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="5721d-117">**Header:** None\</span></span>
<span data-ttu-id="5721d-118">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="5721d-118">**Library:** None\</span></span>
<span data-ttu-id="5721d-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5721d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5721d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5721d-120">See also</span></span>

- [<span data-ttu-id="5721d-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="5721d-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="5721d-122">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="5721d-122">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
