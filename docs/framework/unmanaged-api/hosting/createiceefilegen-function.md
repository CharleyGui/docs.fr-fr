---
title: CreateICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57163ccfcc6dff343a8bbc7d63564ae6b57b5ff6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490501"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="9800c-102">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="9800c-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="9800c-103">Crée un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.</span><span class="sxs-lookup"><span data-stu-id="9800c-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="9800c-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9800c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9800c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9800c-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9800c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9800c-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="9800c-107">[out] Un pointeur vers l’adresse d’un nouveau `ICeeFileGen` objet.</span><span class="sxs-lookup"><span data-stu-id="9800c-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9800c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9800c-108">Return Value</span></span>  
 <span data-ttu-id="9800c-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="9800c-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9800c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9800c-110">Remarks</span></span>  
 <span data-ttu-id="9800c-111">Le `ICeeFileGen` objet est utilisé pour créer de common language runtime (CLR) les fichiers exécutables portables (PE).</span><span class="sxs-lookup"><span data-stu-id="9800c-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="9800c-112">Appelez le [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) fonction détruire le `ICeeFileGen` issue de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9800c-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9800c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9800c-113">Requirements</span></span>  
 <span data-ttu-id="9800c-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9800c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9800c-115">**En-tête :** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="9800c-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="9800c-116">**Bibliothèque :** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="9800c-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="9800c-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9800c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9800c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9800c-118">See also</span></span>

- [<span data-ttu-id="9800c-119">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9800c-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
