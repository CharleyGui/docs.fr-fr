---
title: CoInitializeEE, fonction
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9597b12b0da6df807b2d4eaa42c2035c518b71d9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490625"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="1a7bd-102">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="1a7bd-102">CoInitializeEE Function</span></span>
<span data-ttu-id="1a7bd-103">Garantit que le moteur d’exécution du common language runtime est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="1a7bd-104">Cette fonction est déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="1a7bd-105">Utilisez le [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7bd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a7bd-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a7bd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a7bd-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="1a7bd-108">[in] Parmi les [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a7bd-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a7bd-109">Return Value</span></span>  
 <span data-ttu-id="1a7bd-110">Cette méthode retourne des codes d’erreur COM standard, tel que défini dans Winerror.h et les valeurs dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="1a7bd-111">Code de retour</span><span class="sxs-lookup"><span data-stu-id="1a7bd-111">Return code</span></span>|<span data-ttu-id="1a7bd-112">Description</span><span class="sxs-lookup"><span data-stu-id="1a7bd-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1a7bd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a7bd-113">S_OK</span></span>|<span data-ttu-id="1a7bd-114">Le moteur d’exécution a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="1a7bd-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a7bd-115">S_FALSE</span></span>|<span data-ttu-id="1a7bd-116">Le moteur d’exécution est déjà chargé.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="1a7bd-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a7bd-117">E_FAIL</span></span>|<span data-ttu-id="1a7bd-118">Le moteur d’exécution n’a pas pu être chargé.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a7bd-119">Notes</span><span class="sxs-lookup"><span data-stu-id="1a7bd-119">Remarks</span></span>  
 <span data-ttu-id="1a7bd-120">Cette méthode charge le moteur d’exécution s’il n’a pas été chargé précédemment.</span><span class="sxs-lookup"><span data-stu-id="1a7bd-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a7bd-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a7bd-121">Requirements</span></span>  
 <span data-ttu-id="1a7bd-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a7bd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a7bd-123">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a7bd-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a7bd-124">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a7bd-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a7bd-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a7bd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a7bd-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a7bd-126">See also</span></span>

- [<span data-ttu-id="1a7bd-127">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="1a7bd-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
