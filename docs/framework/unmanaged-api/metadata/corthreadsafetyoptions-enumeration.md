---
title: CorThreadSafetyOptions, énumération
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007505"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="5de37-102">CorThreadSafetyOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="5de37-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="5de37-103">Spécifie des indicateurs permettant de sélectionner des options pour la sécurité des threads.</span><span class="sxs-lookup"><span data-stu-id="5de37-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="5de37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5de37-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="5de37-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5de37-105">Members</span></span>

|<span data-ttu-id="5de37-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5de37-106">Member</span></span>|<span data-ttu-id="5de37-107">Description</span><span class="sxs-lookup"><span data-stu-id="5de37-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="5de37-108">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5de37-108">Default value.</span></span> <span data-ttu-id="5de37-109">Identique à `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="5de37-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="5de37-110">Indique qu’un verrou de lecture/écriture ne peut pas être défini.</span><span class="sxs-lookup"><span data-stu-id="5de37-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="5de37-111">Indique qu’un verrou de lecture/écriture peut être défini.</span><span class="sxs-lookup"><span data-stu-id="5de37-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="5de37-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5de37-112">Requirements</span></span>

<span data-ttu-id="5de37-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5de37-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5de37-114">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5de37-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="5de37-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5de37-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5de37-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5de37-116">See also</span></span>

- [<span data-ttu-id="5de37-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5de37-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
