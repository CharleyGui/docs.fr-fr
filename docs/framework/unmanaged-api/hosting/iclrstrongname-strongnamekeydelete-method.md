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
ms.openlocfilehash: 4e72818be6808c519677192d3744bbc5ec414d0d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135091"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="83892-102">Méthode ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="83892-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="83892-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="83892-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83892-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83892-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83892-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83892-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="83892-106">dans Nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="83892-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83892-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83892-107">Return Value</span></span>  
 <span data-ttu-id="83892-108">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="83892-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83892-109">Notes</span><span class="sxs-lookup"><span data-stu-id="83892-109">Remarks</span></span>  
 <span data-ttu-id="83892-110">Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="83892-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83892-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="83892-111">Requirements</span></span>  
 <span data-ttu-id="83892-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83892-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83892-113">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="83892-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="83892-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83892-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83892-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83892-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83892-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83892-116">See also</span></span>

- [<span data-ttu-id="83892-117">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="83892-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="83892-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="83892-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
