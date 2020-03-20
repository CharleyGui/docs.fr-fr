---
title: Méthode ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181939"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="a3227-102">Méthode ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="a3227-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="a3227-103">Obtient la clé publique d’une paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a3227-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="a3227-104">La paire de clés peut être fournie soit comme un nom de conteneur clé au sein d’un fournisseur de services cryptographiques (CSP) ou comme une collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="a3227-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3227-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3227-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3227-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a3227-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="a3227-107">[dans] Le nom du conteneur clé qui contient la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a3227-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="a3227-108">S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide dans le CSP.</span><span class="sxs-lookup"><span data-stu-id="a3227-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="a3227-109">Dans ce cas, la méthode [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode extrait la clé publique de la paire de clés stockées dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="a3227-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="a3227-110">Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a3227-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a3227-111">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="a3227-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a3227-112">Aucun autre type de clés n’est pris en charge pour le moment.</span><span class="sxs-lookup"><span data-stu-id="a3227-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a3227-113">[dans] Un pointeur à la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a3227-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a3227-114">Cette paire est dans le format `CryptExportKey` créé par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="a3227-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a3227-115">S’il `pbKeyBlob` est nul, `szKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="a3227-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a3227-116">[dans] La taille, dans les `pbKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="a3227-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="a3227-117">[out] Le BLOB clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="a3227-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="a3227-118">Le `ppbPublicKeyBlob` paramètre est attribué par l’heure de l’exécution de la langue commune et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="a3227-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="a3227-119">L’appelant doit libérer la mémoire en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="a3227-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="a3227-120">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="a3227-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3227-121">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a3227-121">Return Value</span></span>  
 <span data-ttu-id="a3227-122">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a3227-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3227-123">Notes </span><span class="sxs-lookup"><span data-stu-id="a3227-123">Remarks</span></span>  
 <span data-ttu-id="a3227-124">La clé publique est contenue dans une structure [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="a3227-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3227-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a3227-125">Requirements</span></span>  
 <span data-ttu-id="a3227-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3227-127">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a3227-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3227-128">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3227-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3227-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3227-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3227-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3227-130">See also</span></span>

- [<span data-ttu-id="a3227-131">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a3227-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a3227-132">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="a3227-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="a3227-133">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a3227-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
