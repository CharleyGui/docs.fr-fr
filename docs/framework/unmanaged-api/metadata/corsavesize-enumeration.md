---
title: CorSaveSize, énumération
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 81d47a3e4d72f991dc15924e7ff1ecc8df2e7322
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706051"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="49d51-102">CorSaveSize, énumération</span><span class="sxs-lookup"><span data-stu-id="49d51-102">CorSaveSize Enumeration</span></span>

<span data-ttu-id="49d51-103">Contient des valeurs indiquant le niveau de précision requis lors de l'interrogation de la taille d'une opération d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="49d51-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49d51-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="49d51-105">Membres</span><span class="sxs-lookup"><span data-stu-id="49d51-105">Members</span></span>  
  
|<span data-ttu-id="49d51-106">Membre</span><span class="sxs-lookup"><span data-stu-id="49d51-106">Member</span></span>|<span data-ttu-id="49d51-107">Description</span><span class="sxs-lookup"><span data-stu-id="49d51-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="49d51-108">Spécifie que la valeur de retour doit être exacte.</span><span class="sxs-lookup"><span data-stu-id="49d51-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="49d51-109">Spécifie que la valeur de retour doit être estimée.</span><span class="sxs-lookup"><span data-stu-id="49d51-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="49d51-110">Spécifie que les types pouvant être éliminés doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="49d51-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49d51-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49d51-111">Requirements</span></span>  

 <span data-ttu-id="49d51-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d51-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d51-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="49d51-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="49d51-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49d51-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49d51-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d51-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d51-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49d51-116">See also</span></span>

- [<span data-ttu-id="49d51-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="49d51-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
