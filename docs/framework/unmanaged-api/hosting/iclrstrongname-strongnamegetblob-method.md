---
title: Méthode ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 9d7f1a71658b53a1b4167c767eb89c873308421b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135125"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="7a252-102">Méthode ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="7a252-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="7a252-103">Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7a252-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a252-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a252-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a252-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7a252-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7a252-106">dans Chemin d’accès valide au fichier exécutable à charger.</span><span class="sxs-lookup"><span data-stu-id="7a252-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="7a252-107">dans Mémoire tampon dans laquelle charger le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="7a252-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="7a252-108">[in, out] Taille maximale demandée, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7a252-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="7a252-109">Lors du retour, taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7a252-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a252-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7a252-110">Return Value</span></span>  
 <span data-ttu-id="7a252-111">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="7a252-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a252-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="7a252-112">Requirements</span></span>  
 <span data-ttu-id="7a252-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a252-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a252-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="7a252-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7a252-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7a252-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a252-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a252-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a252-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a252-117">See also</span></span>

- [<span data-ttu-id="7a252-118">StrongNameGetBlobFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="7a252-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="7a252-119">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="7a252-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
