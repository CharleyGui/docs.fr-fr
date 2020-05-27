---
title: CorPropertyAttr, énumération
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007531"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="3cc51-102">CorPropertyAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="3cc51-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="3cc51-103">Contient des valeurs qui décrivent les métadonnées d'une propriété.</span><span class="sxs-lookup"><span data-stu-id="3cc51-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cc51-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="3cc51-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3cc51-105">Members</span></span>  
  
|<span data-ttu-id="3cc51-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3cc51-106">Member</span></span>|<span data-ttu-id="3cc51-107">Description</span><span class="sxs-lookup"><span data-stu-id="3cc51-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="3cc51-108">Spécifie que la propriété est spéciale et que son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="3cc51-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="3cc51-109">Réservé à un usage interne par la common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3cc51-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="3cc51-110">Spécifie que l’common language runtime les API internes de métadonnées doivent vérifier l’encodage du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3cc51-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="3cc51-111">Spécifie que la propriété a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3cc51-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="3cc51-112">Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="3cc51-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3cc51-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3cc51-113">Requirements</span></span>  
 <span data-ttu-id="3cc51-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc51-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc51-115">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3cc51-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3cc51-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc51-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc51-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cc51-117">See also</span></span>

- [<span data-ttu-id="3cc51-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3cc51-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
