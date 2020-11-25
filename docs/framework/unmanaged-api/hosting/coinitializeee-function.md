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
ms.openlocfilehash: 707e182e62f4a7b7b813e6b288c6825b0d3d2eab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731746"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="b9ecc-102">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="b9ecc-102">CoInitializeEE Function</span></span>

<span data-ttu-id="b9ecc-103">Garantit que le moteur d’exécution de common language runtime est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="b9ecc-104">Cette fonction est déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b9ecc-105">Utilisez à la place la méthode [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9ecc-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ecc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9ecc-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ecc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9ecc-107">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="b9ecc-108">dans Une des constantes d’énumération [COINITIEE,](../metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b9ecc-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9ecc-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b9ecc-109">Return Value</span></span>  

 <span data-ttu-id="b9ecc-110">Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans Winerror. h, ainsi que les valeurs du tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="b9ecc-111">Code de retour</span><span class="sxs-lookup"><span data-stu-id="b9ecc-111">Return code</span></span>|<span data-ttu-id="b9ecc-112">Description</span><span class="sxs-lookup"><span data-stu-id="b9ecc-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b9ecc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9ecc-113">S_OK</span></span>|<span data-ttu-id="b9ecc-114">Le moteur d’exécution a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="b9ecc-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b9ecc-115">S_FALSE</span></span>|<span data-ttu-id="b9ecc-116">Le moteur d’exécution est déjà chargé.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="b9ecc-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9ecc-117">E_FAIL</span></span>|<span data-ttu-id="b9ecc-118">Le moteur d’exécution n’a pas pu être chargé.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9ecc-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9ecc-119">Remarks</span></span>  

 <span data-ttu-id="b9ecc-120">Cette méthode charge le moteur d’exécution s’il n’a pas été chargé précédemment.</span><span class="sxs-lookup"><span data-stu-id="b9ecc-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ecc-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9ecc-121">Requirements</span></span>  

 <span data-ttu-id="b9ecc-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ecc-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ecc-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9ecc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9ecc-124">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9ecc-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9ecc-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ecc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ecc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9ecc-126">See also</span></span>

- [<span data-ttu-id="b9ecc-127">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="b9ecc-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
