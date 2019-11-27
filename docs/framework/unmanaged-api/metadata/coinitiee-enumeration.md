---
title: COINITIEE, énumération
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444101"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="9b6da-102">COINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="9b6da-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="9b6da-103">Spécifie les constantes utilisées par [CoInitializeEE,](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) lors de l’initialisation du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9b6da-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b6da-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="9b6da-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b6da-105">Members</span></span>  
  
|<span data-ttu-id="9b6da-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b6da-106">Member</span></span>|<span data-ttu-id="9b6da-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b6da-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="9b6da-108">Mode d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b6da-108">Default initialization mode.</span></span> <span data-ttu-id="9b6da-109">Cela initialise le runtime et crée le <xref:System.AppDomain>par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b6da-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="9b6da-110">Initialise pour exécuter une DLL managée.</span><span class="sxs-lookup"><span data-stu-id="9b6da-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="9b6da-111">Initialise pour exécuter un EXE managé.</span><span class="sxs-lookup"><span data-stu-id="9b6da-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="9b6da-112">Cela initialise le runtime, mais ne crée pas le <xref:System.AppDomain>par défaut, qui est créé après l’entrée de la routine principale de l’EXE.</span><span class="sxs-lookup"><span data-stu-id="9b6da-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b6da-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b6da-113">Requirements</span></span>  
 <span data-ttu-id="9b6da-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6da-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6da-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b6da-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b6da-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b6da-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b6da-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6da-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6da-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b6da-118">See also</span></span>

- [<span data-ttu-id="9b6da-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="9b6da-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
