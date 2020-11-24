---
title: CorNativeLinkType, énumération
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: c155373f7da47e904c94a44efa2fba42309d4218
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671354"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9081d-102">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="9081d-102">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="9081d-103">Fournit des valeurs qui indiquent le type lié en code natif.</span><span class="sxs-lookup"><span data-stu-id="9081d-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9081d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9081d-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="9081d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9081d-105">Members</span></span>  
  
|<span data-ttu-id="9081d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9081d-106">Member</span></span>|<span data-ttu-id="9081d-107">Description</span><span class="sxs-lookup"><span data-stu-id="9081d-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9081d-108">Indique qu’aucun des mots clés n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9081d-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9081d-109">Indique qu’un mot clé ANSI est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9081d-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9081d-110">Indique qu’un mot clé Unicode est spécifié</span><span class="sxs-lookup"><span data-stu-id="9081d-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9081d-111">Indique qu’un mot clé auto est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9081d-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9081d-112">Indique qu’un mot clé OLE est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9081d-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9081d-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="9081d-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9081d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9081d-114">Requirements</span></span>  

 <span data-ttu-id="9081d-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9081d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9081d-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9081d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9081d-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9081d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9081d-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9081d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9081d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9081d-119">See also</span></span>

- [<span data-ttu-id="9081d-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="9081d-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
