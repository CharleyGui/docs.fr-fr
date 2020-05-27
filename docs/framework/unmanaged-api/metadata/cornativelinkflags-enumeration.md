---
title: CorNativeLinkFlags, énumération
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9211af4726617598f3dd8772383cade6368e6c08
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007622"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="290c8-102">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="290c8-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="290c8-103">Fournit des valeurs d'indicateur utilisées par l'éditeur de liens lors de la liaison du code natif.</span><span class="sxs-lookup"><span data-stu-id="290c8-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="290c8-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="290c8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="290c8-105">Members</span></span>  
  
|<span data-ttu-id="290c8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="290c8-106">Member</span></span>|<span data-ttu-id="290c8-107">Description</span><span class="sxs-lookup"><span data-stu-id="290c8-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="290c8-108">N’indique aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="290c8-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="290c8-109">Indique un `setLastError` mot clé.</span><span class="sxs-lookup"><span data-stu-id="290c8-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="290c8-110">Indique un `nomangle` mot clé.</span><span class="sxs-lookup"><span data-stu-id="290c8-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="290c8-111">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="290c8-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="290c8-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="290c8-112">Requirements</span></span>  
 <span data-ttu-id="290c8-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="290c8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="290c8-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="290c8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="290c8-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="290c8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="290c8-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="290c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290c8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="290c8-117">See also</span></span>

- [<span data-ttu-id="290c8-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="290c8-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
