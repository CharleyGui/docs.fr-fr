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
ms.openlocfilehash: 46345ae570673c9c9c0c58fb6edea1464ba8dd91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671692"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="ac67f-102">Méthode ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="ac67f-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="ac67f-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac67f-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac67f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac67f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac67f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac67f-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="ac67f-106">dans Nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ac67f-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac67f-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ac67f-107">Return Value</span></span>  

 <span data-ttu-id="ac67f-108">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="ac67f-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac67f-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ac67f-109">Remarks</span></span>  

 <span data-ttu-id="ac67f-110">Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="ac67f-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac67f-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac67f-111">Requirements</span></span>  

 <span data-ttu-id="ac67f-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac67f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac67f-113">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="ac67f-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ac67f-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac67f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac67f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac67f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac67f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac67f-116">See also</span></span>

- [<span data-ttu-id="ac67f-117">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="ac67f-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="ac67f-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ac67f-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
