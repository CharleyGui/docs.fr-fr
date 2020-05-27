---
title: CVStruct, structure
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 84791eba7c95d3278bd4650bd7d660e98fcb79d8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008914"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="a7cdd-102">CVStruct, structure</span><span class="sxs-lookup"><span data-stu-id="a7cdd-102">CVStruct Structure</span></span>
<span data-ttu-id="a7cdd-103">Contient des informations utilisées lors de l'installation d'un module ou d'une image composite.</span><span class="sxs-lookup"><span data-stu-id="a7cdd-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7cdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7cdd-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="a7cdd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a7cdd-105">Members</span></span>  
  
|<span data-ttu-id="a7cdd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a7cdd-106">Member</span></span>|<span data-ttu-id="a7cdd-107">Description</span><span class="sxs-lookup"><span data-stu-id="a7cdd-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a7cdd-108">Majeure</span><span class="sxs-lookup"><span data-stu-id="a7cdd-108">Major</span></span>|<span data-ttu-id="a7cdd-109">Numéro de build de la version principale.</span><span class="sxs-lookup"><span data-stu-id="a7cdd-109">Major version build number.</span></span>|  
|<span data-ttu-id="a7cdd-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="a7cdd-110">Minor</span></span>|<span data-ttu-id="a7cdd-111">Numéro de build de la version mineure.</span><span class="sxs-lookup"><span data-stu-id="a7cdd-111">Minor version build number.</span></span>|  
|<span data-ttu-id="a7cdd-112">Sub</span><span class="sxs-lookup"><span data-stu-id="a7cdd-112">Sub</span></span>|<span data-ttu-id="a7cdd-113">Numéro de sous-Build.</span><span class="sxs-lookup"><span data-stu-id="a7cdd-113">Sub-build number.</span></span>|  
|<span data-ttu-id="a7cdd-114">Build</span><span class="sxs-lookup"><span data-stu-id="a7cdd-114">Build</span></span>|<span data-ttu-id="a7cdd-115">Numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="a7cdd-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7cdd-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a7cdd-116">Requirements</span></span>  
 <span data-ttu-id="a7cdd-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7cdd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7cdd-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a7cdd-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7cdd-119">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7cdd-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7cdd-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7cdd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7cdd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7cdd-121">See also</span></span>

- [<span data-ttu-id="a7cdd-122">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a7cdd-122">Metadata Structures</span></span>](metadata-structures.md)
