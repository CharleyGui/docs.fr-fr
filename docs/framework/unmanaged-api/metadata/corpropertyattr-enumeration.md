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
ms.openlocfilehash: 95a798d662b44cf2e088af84d3b1eec97da8e7fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177941"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="d40ee-102">CorPropertyAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="d40ee-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="d40ee-103">Contient des valeurs qui décrivent les métadonnées d'une propriété.</span><span class="sxs-lookup"><span data-stu-id="d40ee-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d40ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d40ee-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="d40ee-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d40ee-105">Members</span></span>  
  
|<span data-ttu-id="d40ee-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d40ee-106">Member</span></span>|<span data-ttu-id="d40ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="d40ee-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="d40ee-108">Précise que la propriété est spéciale, et que son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="d40ee-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="d40ee-109">Réservé à l’utilisation interne par l’heure courante de la langue commune.</span><span class="sxs-lookup"><span data-stu-id="d40ee-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="d40ee-110">Spécifie que les métadonnées internes de métadonnées de langage courant doivent vérifier l’encodage du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d40ee-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="d40ee-111">Spécifie que la propriété a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d40ee-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="d40ee-112">Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="d40ee-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d40ee-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d40ee-113">Requirements</span></span>  
 <span data-ttu-id="d40ee-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d40ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d40ee-115">**En-tête:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d40ee-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d40ee-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d40ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40ee-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d40ee-117">See also</span></span>

- [<span data-ttu-id="d40ee-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="d40ee-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
