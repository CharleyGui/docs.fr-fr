---
title: Fonction EndEnumeration (référence des API non managées)
description: La fonction EndEnumeration met fin à une énumération.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b9fd1f094c8fb56c94421a07437aa25a3549c487
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132044"
---
# <a name="endenumeration-function"></a><span data-ttu-id="fdda6-103">EndEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="fdda6-103">EndEnumeration function</span></span>

<span data-ttu-id="fdda6-104">Termine une séquence d’énumération démarrée avec un appel à la [fonction BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="fdda6-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fdda6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdda6-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="fdda6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fdda6-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="fdda6-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="fdda6-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="fdda6-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="fdda6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="fdda6-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fdda6-109">Return value</span></span>

<span data-ttu-id="fdda6-110">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="fdda6-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fdda6-111">Constante</span><span class="sxs-lookup"><span data-stu-id="fdda6-111">Constant</span></span>  |<span data-ttu-id="fdda6-112">valeur</span><span class="sxs-lookup"><span data-stu-id="fdda6-112">Value</span></span>  |<span data-ttu-id="fdda6-113">Description</span><span class="sxs-lookup"><span data-stu-id="fdda6-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="fdda6-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fdda6-114">0x80041001</span></span> | <span data-ttu-id="fdda6-115">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fdda6-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fdda6-116">0</span><span class="sxs-lookup"><span data-stu-id="fdda6-116">0</span></span> | <span data-ttu-id="fdda6-117">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="fdda6-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="fdda6-118">Notes</span><span class="sxs-lookup"><span data-stu-id="fdda6-118">Remarks</span></span>

<span data-ttu-id="fdda6-119">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="fdda6-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="fdda6-120">Un appel à la fonction `EndEnumeration` n’est pas obligatoire, mais il est recommandé, car il libère les ressources associées à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="fdda6-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="fdda6-121">Toutefois, les ressources sont désallouées automatiquement lorsque l’énumération suivante est démarrée ou lorsque l’objet est libéré.</span><span class="sxs-lookup"><span data-stu-id="fdda6-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="fdda6-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="fdda6-122">Requirements</span></span>

<span data-ttu-id="fdda6-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdda6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="fdda6-124">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="fdda6-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="fdda6-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fdda6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fdda6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdda6-126">See also</span></span>

- [<span data-ttu-id="fdda6-127">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="fdda6-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
