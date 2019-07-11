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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23f5a2b6b0970f3cb64ee339e6a1a409354a60e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780953"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="96a73-102">COINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="96a73-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="96a73-103">Spécifie les constantes utilisées par [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) lors de l’initialisation du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="96a73-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96a73-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="96a73-105">Membres</span><span class="sxs-lookup"><span data-stu-id="96a73-105">Members</span></span>  
  
|<span data-ttu-id="96a73-106">Membre</span><span class="sxs-lookup"><span data-stu-id="96a73-106">Member</span></span>|<span data-ttu-id="96a73-107">Description</span><span class="sxs-lookup"><span data-stu-id="96a73-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="96a73-108">Mode d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="96a73-108">Default initialization mode.</span></span> <span data-ttu-id="96a73-109">Initialise l’exécution et crée la valeur par défaut <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="96a73-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="96a73-110">Initialise l’exécution d’une DLL managée.</span><span class="sxs-lookup"><span data-stu-id="96a73-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="96a73-111">Initialise l’exécution d’un EXE managé.</span><span class="sxs-lookup"><span data-stu-id="96a73-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="96a73-112">Cela initialise le runtime, mais ne crée pas la valeur par défaut <xref:System.AppDomain>, qui est créé après avoir entré la routine principale de l’EXE.</span><span class="sxs-lookup"><span data-stu-id="96a73-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96a73-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96a73-113">Requirements</span></span>  
 <span data-ttu-id="96a73-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a73-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a73-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96a73-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96a73-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96a73-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96a73-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a73-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a73-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96a73-118">See also</span></span>

- [<span data-ttu-id="96a73-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="96a73-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
