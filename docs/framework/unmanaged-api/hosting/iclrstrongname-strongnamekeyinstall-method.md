---
title: Méthode ICLRStrongName::StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 2a76377857c3cf1e40a328b9a13fb4834321707e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899567"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="ed3d5-102">Méthode ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="ed3d5-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="ed3d5-103">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed3d5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed3d5-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="ed3d5-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ed3d5-106">dans Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-106">[in] The name of the key container.</span></span> <span data-ttu-id="ed3d5-107">`wszKeyContainer` doit être une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ed3d5-108">dans Paire de clés binaires.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ed3d5-109">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed3d5-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ed3d5-110">Return Value</span></span>  
 <span data-ttu-id="ed3d5-111">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="ed3d5-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed3d5-112">Notes</span><span class="sxs-lookup"><span data-stu-id="ed3d5-112">Remarks</span></span>  
 <span data-ttu-id="ed3d5-113">Utilisez la méthode [ICLRStrongName :: StrongNameKeyDelete (](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) pour supprimer le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="ed3d5-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed3d5-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ed3d5-114">Requirements</span></span>  
 <span data-ttu-id="ed3d5-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed3d5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed3d5-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="ed3d5-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ed3d5-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed3d5-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed3d5-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed3d5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3d5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed3d5-119">See also</span></span>

- [<span data-ttu-id="ed3d5-120">StrongNameKeyDelete, méthode</span><span class="sxs-lookup"><span data-stu-id="ed3d5-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="ed3d5-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ed3d5-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
