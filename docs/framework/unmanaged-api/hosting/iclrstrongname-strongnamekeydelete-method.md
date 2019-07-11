---
title: Méthode ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540fda24a8085a3066dc0485228d3ea3bc56fb98
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747779"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="2d109-102">Méthode ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="2d109-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="2d109-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="2d109-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d109-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d109-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d109-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d109-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="2d109-106">[in] Le nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2d109-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d109-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d109-107">Return Value</span></span>  
 <span data-ttu-id="2d109-108">`S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="2d109-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d109-109">Notes</span><span class="sxs-lookup"><span data-stu-id="2d109-109">Remarks</span></span>  
 <span data-ttu-id="2d109-110">Utilisez le [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) méthode pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="2d109-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d109-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d109-111">Requirements</span></span>  
 <span data-ttu-id="2d109-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d109-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d109-113">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d109-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d109-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d109-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d109-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d109-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d109-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d109-116">See also</span></span>

- [<span data-ttu-id="2d109-117">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="2d109-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="2d109-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2d109-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
