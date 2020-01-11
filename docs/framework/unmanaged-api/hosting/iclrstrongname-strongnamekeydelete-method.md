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
ms.openlocfilehash: 95098cbb060c06d2d5a5a4c04b6fa9017bca66a1
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899594"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="01553-102">Méthode ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="01553-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="01553-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="01553-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01553-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01553-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01553-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="01553-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="01553-106">dans Nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="01553-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01553-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="01553-107">Return Value</span></span>  
 <span data-ttu-id="01553-108">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="01553-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01553-109">Notes</span><span class="sxs-lookup"><span data-stu-id="01553-109">Remarks</span></span>  
 <span data-ttu-id="01553-110">Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="01553-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01553-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="01553-111">Requirements</span></span>  
 <span data-ttu-id="01553-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01553-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01553-113">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="01553-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="01553-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01553-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01553-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01553-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01553-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01553-116">See also</span></span>

- [<span data-ttu-id="01553-117">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="01553-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="01553-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="01553-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
