---
title: CorRegFlags, énumération
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: d8d7a43848929e49a8cb48fb957f37213ac78f2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007349"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="a56d5-102">CorRegFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="a56d5-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="a56d5-103">Fournit des valeurs d’indicateur utilisées pour l’inscription lors de l’installation d’un module ou d’une image composite.</span><span class="sxs-lookup"><span data-stu-id="a56d5-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a56d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a56d5-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a56d5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a56d5-105">Members</span></span>  
  
|<span data-ttu-id="a56d5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a56d5-106">Member</span></span>|<span data-ttu-id="a56d5-107">Description</span><span class="sxs-lookup"><span data-stu-id="a56d5-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="a56d5-108">Spécifie que les fichiers ne doivent pas être copiés dans la destination.</span><span class="sxs-lookup"><span data-stu-id="a56d5-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="a56d5-109">Spécifie que le module ou composite est une configuration.</span><span class="sxs-lookup"><span data-stu-id="a56d5-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="a56d5-110">Spécifie que le module ou le composite a des références de classe.</span><span class="sxs-lookup"><span data-stu-id="a56d5-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a56d5-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a56d5-111">Requirements</span></span>  
 <span data-ttu-id="a56d5-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a56d5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a56d5-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a56d5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a56d5-114">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a56d5-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a56d5-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56d5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a56d5-116">See also</span></span>

- [<span data-ttu-id="a56d5-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a56d5-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
