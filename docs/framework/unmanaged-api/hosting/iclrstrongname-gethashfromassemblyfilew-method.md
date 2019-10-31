---
title: Méthode ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 43a5cd57a8eeaba70f1bb1ffb9cab5bb1a067914
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130950"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="fcd04-102">Méthode ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="fcd04-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="fcd04-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="fcd04-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcd04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcd04-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcd04-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fcd04-106">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="fcd04-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="fcd04-107">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="fcd04-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fcd04-108">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="fcd04-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="fcd04-109">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="fcd04-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fcd04-110">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="fcd04-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fcd04-111">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="fcd04-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fcd04-112">à Taille retournée, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fcd04-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcd04-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fcd04-113">Return Value</span></span>  
 <span data-ttu-id="fcd04-114">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="fcd04-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd04-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="fcd04-115">Requirements</span></span>  
 <span data-ttu-id="fcd04-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd04-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd04-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="fcd04-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fcd04-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fcd04-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcd04-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd04-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd04-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcd04-120">See also</span></span>

- [<span data-ttu-id="fcd04-121">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="fcd04-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="fcd04-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="fcd04-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
