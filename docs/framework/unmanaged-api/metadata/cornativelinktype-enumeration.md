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
ms.openlocfilehash: 29f2401e2e3faccae05ca5249fcd7d9e89aacb46
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007609"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="1ea29-102">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="1ea29-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="1ea29-103">Fournit des valeurs qui indiquent le type lié en code natif.</span><span class="sxs-lookup"><span data-stu-id="1ea29-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ea29-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1ea29-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1ea29-105">Members</span></span>  
  
|<span data-ttu-id="1ea29-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1ea29-106">Member</span></span>|<span data-ttu-id="1ea29-107">Description</span><span class="sxs-lookup"><span data-stu-id="1ea29-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="1ea29-108">Indique qu’aucun des mots clés n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ea29-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="1ea29-109">Indique qu’un mot clé ANSI est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ea29-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="1ea29-110">Indique qu’un mot clé Unicode est spécifié</span><span class="sxs-lookup"><span data-stu-id="1ea29-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="1ea29-111">Indique qu’un mot clé auto est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ea29-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="1ea29-112">Indique qu’un mot clé OLE est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ea29-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="1ea29-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="1ea29-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ea29-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1ea29-114">Requirements</span></span>  
 <span data-ttu-id="1ea29-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea29-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea29-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1ea29-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ea29-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ea29-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea29-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea29-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ea29-119">See also</span></span>

- [<span data-ttu-id="1ea29-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="1ea29-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
