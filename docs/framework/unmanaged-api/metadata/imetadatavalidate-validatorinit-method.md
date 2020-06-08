---
title: IMetaDataValidate::ValidatorInit, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 687f33c364f9730a554a41ade1ca2b78e33ffdc5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489678"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="43ae2-102">IMetaDataValidate::ValidatorInit, méthode</span><span class="sxs-lookup"><span data-stu-id="43ae2-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="43ae2-103">Définit un indicateur qui spécifie le type du module dans la portée de métadonnées actuelle et enregistre la méthode de rappel spécifiée pour les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="43ae2-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43ae2-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ae2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43ae2-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="43ae2-106">dans Valeur de l’énumération [CorValidatorModuleType,](corvalidatormoduletype-enumeration.md) qui spécifie le type du module dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="43ae2-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="43ae2-107">dans Pointeur vers une instance [IUnknown](/cpp/atl/iunknown) qui sert de rappel de fonction pour les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="43ae2-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ae2-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="43ae2-108">Requirements</span></span>  
 <span data-ttu-id="43ae2-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ae2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ae2-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="43ae2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43ae2-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43ae2-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43ae2-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ae2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ae2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43ae2-113">See also</span></span>

- [<span data-ttu-id="43ae2-114">IMetaDataValidate, interface</span><span class="sxs-lookup"><span data-stu-id="43ae2-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
