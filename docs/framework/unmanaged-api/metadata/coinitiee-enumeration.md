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
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005906"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="9b5fc-102">COINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="9b5fc-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="9b5fc-103">Spécifie les constantes utilisées par [CoInitializeEE,](../hosting/coinitializeee-function.md) lors de l’initialisation du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9b5fc-103">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b5fc-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="9b5fc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b5fc-105">Members</span></span>  
  
|<span data-ttu-id="9b5fc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b5fc-106">Member</span></span>|<span data-ttu-id="9b5fc-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b5fc-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="9b5fc-108">Mode d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b5fc-108">Default initialization mode.</span></span> <span data-ttu-id="9b5fc-109">Cela initialise le runtime et crée la valeur par défaut <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="9b5fc-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="9b5fc-110">Initialise pour exécuter une DLL managée.</span><span class="sxs-lookup"><span data-stu-id="9b5fc-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="9b5fc-111">Initialise pour exécuter un EXE managé.</span><span class="sxs-lookup"><span data-stu-id="9b5fc-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="9b5fc-112">Cela initialise le runtime, mais ne crée pas la valeur par défaut <xref:System.AppDomain> , qui est créée après l’entrée de la routine principale de l’exe.</span><span class="sxs-lookup"><span data-stu-id="9b5fc-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b5fc-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b5fc-113">Requirements</span></span>  
 <span data-ttu-id="9b5fc-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b5fc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b5fc-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b5fc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b5fc-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b5fc-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b5fc-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b5fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5fc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b5fc-118">See also</span></span>

- [<span data-ttu-id="9b5fc-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="9b5fc-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
