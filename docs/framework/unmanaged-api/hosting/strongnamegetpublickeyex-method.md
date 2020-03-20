---
title: StrongNameGetPublicKeyEx, méthode
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176225"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="e3c67-102">StrongNameGetPublicKeyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="e3c67-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="e3c67-103">Obtient la clé publique d’une paire de clés publique/privée, et spécifie un algorithme de hachage et un algorithme de signature.</span><span class="sxs-lookup"><span data-stu-id="e3c67-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3c67-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c67-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3c67-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="e3c67-106">[dans] Le nom du conteneur clé qui contient la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="e3c67-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="e3c67-107">S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide au sein du fournisseur de services cryptographiques (CSP).</span><span class="sxs-lookup"><span data-stu-id="e3c67-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="e3c67-108">Dans ce cas, la `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="e3c67-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="e3c67-109">Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).</span><span class="sxs-lookup"><span data-stu-id="e3c67-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="e3c67-110">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="e3c67-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="e3c67-111">Aucun autre type de clés n’est pris en charge pour le moment.</span><span class="sxs-lookup"><span data-stu-id="e3c67-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="e3c67-112">[dans] Un pointeur à la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="e3c67-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="e3c67-113">Cette paire est dans le format `CryptExportKey` créé par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="e3c67-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="e3c67-114">S’il `pbKeyBlob` est nul, `szKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="e3c67-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="e3c67-115">[dans] La taille, dans les `pbKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="e3c67-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="e3c67-116">[out] Le BLOB clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="e3c67-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="e3c67-117">Le `ppbPublicKeyBlob` paramètre est attribué par l’heure de l’exécution de la langue commune et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e3c67-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="e3c67-118">L’appelant doit libérer la mémoire en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="e3c67-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="e3c67-119">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="e3c67-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="e3c67-120">[dans] L’algorithme de hachage d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="e3c67-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="e3c67-121">Consultez la section Remarques pour une liste de valeurs acceptées.</span><span class="sxs-lookup"><span data-stu-id="e3c67-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="e3c67-122">[dans] Réservé à une utilisation future; par défaut à null.</span><span class="sxs-lookup"><span data-stu-id="e3c67-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3c67-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e3c67-123">Return Value</span></span>  
 <span data-ttu-id="e3c67-124">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="e3c67-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3c67-125">Notes </span><span class="sxs-lookup"><span data-stu-id="e3c67-125">Remarks</span></span>  
 <span data-ttu-id="e3c67-126">La clé publique est contenue dans une structure [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="e3c67-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3c67-127">Notes </span><span class="sxs-lookup"><span data-stu-id="e3c67-127">Remarks</span></span>  
 <span data-ttu-id="e3c67-128">Le tableau suivant montre l’ensemble `uHashAlgId` des valeurs acceptées pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3c67-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="e3c67-129">Nom</span><span class="sxs-lookup"><span data-stu-id="e3c67-129">Name</span></span>|<span data-ttu-id="e3c67-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="e3c67-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="e3c67-131">None</span><span class="sxs-lookup"><span data-stu-id="e3c67-131">None</span></span>|<span data-ttu-id="e3c67-132">0</span><span class="sxs-lookup"><span data-stu-id="e3c67-132">0</span></span>|  
|<span data-ttu-id="e3c67-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="e3c67-133">SHA-1</span></span>|<span data-ttu-id="e3c67-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="e3c67-134">0x8004</span></span>|  
|<span data-ttu-id="e3c67-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="e3c67-135">SHA-256</span></span>|<span data-ttu-id="e3c67-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="e3c67-136">0x800c</span></span>|  
|<span data-ttu-id="e3c67-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="e3c67-137">SHA-384</span></span>|<span data-ttu-id="e3c67-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="e3c67-138">0x800d</span></span>|  
|<span data-ttu-id="e3c67-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="e3c67-139">SHA-512</span></span>|<span data-ttu-id="e3c67-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="e3c67-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3c67-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3c67-141">Requirements</span></span>  
 <span data-ttu-id="e3c67-142">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c67-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c67-143">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e3c67-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e3c67-144">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3c67-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3c67-145">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c67-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c67-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3c67-146">See also</span></span>

- [<span data-ttu-id="e3c67-147">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="e3c67-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="e3c67-148">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="e3c67-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="e3c67-149">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="e3c67-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="e3c67-150">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="e3c67-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
