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
ms.openlocfilehash: 693a5831934647256ac48c8f3a2d30325dee4349
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135034"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="1a01b-102">Méthode ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="1a01b-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="1a01b-103">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a01b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a01b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a01b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a01b-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="1a01b-106">dans Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1a01b-106">[in] The name of the key container.</span></span> <span data-ttu-id="1a01b-107">`wszKeyContainer` doit être une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="1a01b-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1a01b-108">dans Paire de clés binaires.</span><span class="sxs-lookup"><span data-stu-id="1a01b-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1a01b-109">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1a01b-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a01b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a01b-110">Return Value</span></span>  
 <span data-ttu-id="1a01b-111">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="1a01b-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a01b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1a01b-112">Remarks</span></span>  
 <span data-ttu-id="1a01b-113">Utilisez la méthode [ICLRStrongName :: StrongNameKeyDelete (](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) pour supprimer le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1a01b-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a01b-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="1a01b-114">Requirements</span></span>  
 <span data-ttu-id="1a01b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a01b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a01b-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="1a01b-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1a01b-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a01b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a01b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a01b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a01b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a01b-119">See also</span></span>

- [<span data-ttu-id="1a01b-120">StrongNameKeyDelete, méthode</span><span class="sxs-lookup"><span data-stu-id="1a01b-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="1a01b-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="1a01b-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
