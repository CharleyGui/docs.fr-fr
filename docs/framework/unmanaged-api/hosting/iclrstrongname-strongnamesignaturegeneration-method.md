---
title: Méthode ICLRStrongName::StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178049"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="a9f1f-102">Méthode ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="a9f1f-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="a9f1f-103">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9f1f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9f1f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9f1f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a9f1f-106">[dans] Le chemin vers le fichier qui contient le manifeste de l’assemblage pour lequel la signature du nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="a9f1f-107">[dans] Le nom du conteneur clé qui contient la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="a9f1f-108">S’il `pbKeyBlob` `wszKeyContainer` est nul, doit spécifier un conteneur valide au sein du fournisseur de services cryptographiques (CSP).</span><span class="sxs-lookup"><span data-stu-id="a9f1f-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="a9f1f-109">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="a9f1f-110">Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a9f1f-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a9f1f-111">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a9f1f-112">Aucun autre type de clés n’est pris en charge pour le moment.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a9f1f-113">[dans] Un pointeur à la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a9f1f-114">Cette paire est dans le format `CryptExportKey` créé par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a9f1f-115">S’il `pbKeyBlob` est nul, `wszKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a9f1f-116">[dans] La taille, dans les `pbKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="a9f1f-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="a9f1f-117">[out] Un pointeur à l’endroit où le temps d’exécution de langue commune renvoie la signature.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="a9f1f-118">Si `ppbSignatureBlob` elle est nulle, le temps d’exécution stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="a9f1f-119">Si `ppbSignatureBlob` elle n’est pas nulle, le runtime de langue commune alloue l’espace pour retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="a9f1f-120">L’appelant doit libérer cet espace en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="a9f1f-121">[out] La taille, dans les octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9f1f-122">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a9f1f-122">Return Value</span></span>  
 <span data-ttu-id="a9f1f-123">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a9f1f-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9f1f-124">Notes </span><span class="sxs-lookup"><span data-stu-id="a9f1f-124">Remarks</span></span>  
 <span data-ttu-id="a9f1f-125">Spécifier null pour `wszFilePath` calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="a9f1f-126">La signature peut être stockée directement dans le fichier, soit retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f1f-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9f1f-127">Requirements</span></span>  
 <span data-ttu-id="a9f1f-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f1f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f1f-129">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a9f1f-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a9f1f-130">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9f1f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f1f-131">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f1f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f1f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9f1f-132">See also</span></span>

- [<span data-ttu-id="a9f1f-133">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="a9f1f-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="a9f1f-134">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a9f1f-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
