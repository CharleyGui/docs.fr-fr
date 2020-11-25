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
ms.openlocfilehash: db36b94fafe20b58b9bcbb886b8d285326960f67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715574"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="b68ca-102">CVStruct, structure</span><span class="sxs-lookup"><span data-stu-id="b68ca-102">CVStruct Structure</span></span>

<span data-ttu-id="b68ca-103">Contient des informations utilisées lors de l'installation d'un module ou d'une image composite.</span><span class="sxs-lookup"><span data-stu-id="b68ca-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b68ca-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="b68ca-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b68ca-105">Members</span></span>  
  
|<span data-ttu-id="b68ca-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b68ca-106">Member</span></span>|<span data-ttu-id="b68ca-107">Description</span><span class="sxs-lookup"><span data-stu-id="b68ca-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b68ca-108">Majeure</span><span class="sxs-lookup"><span data-stu-id="b68ca-108">Major</span></span>|<span data-ttu-id="b68ca-109">Numéro de build de la version principale.</span><span class="sxs-lookup"><span data-stu-id="b68ca-109">Major version build number.</span></span>|  
|<span data-ttu-id="b68ca-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="b68ca-110">Minor</span></span>|<span data-ttu-id="b68ca-111">Numéro de build de la version mineure.</span><span class="sxs-lookup"><span data-stu-id="b68ca-111">Minor version build number.</span></span>|  
|<span data-ttu-id="b68ca-112">Sub</span><span class="sxs-lookup"><span data-stu-id="b68ca-112">Sub</span></span>|<span data-ttu-id="b68ca-113">Numéro de sous-Build.</span><span class="sxs-lookup"><span data-stu-id="b68ca-113">Sub-build number.</span></span>|  
|<span data-ttu-id="b68ca-114">Build</span><span class="sxs-lookup"><span data-stu-id="b68ca-114">Build</span></span>|<span data-ttu-id="b68ca-115">Numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="b68ca-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b68ca-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b68ca-116">Requirements</span></span>  

 <span data-ttu-id="b68ca-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68ca-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68ca-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b68ca-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b68ca-119">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b68ca-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b68ca-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68ca-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68ca-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b68ca-121">See also</span></span>

- [<span data-ttu-id="b68ca-122">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b68ca-122">Metadata Structures</span></span>](metadata-structures.md)
