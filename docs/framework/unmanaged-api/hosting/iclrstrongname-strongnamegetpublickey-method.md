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
ms.openlocfilehash: fd7f95ea01de397509c2a7b5fc08c0ac401a8da9
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899610"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="5803e-102">Méthode ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="5803e-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="5803e-103">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="5803e-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="5803e-104">La paire de clés peut être fournie en tant que nom de conteneur de clé dans un fournisseur de services de chiffrement (CSP) ou en tant que collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="5803e-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5803e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5803e-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5803e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5803e-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="5803e-107">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="5803e-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="5803e-108">Si `pbKeyBlob` a la valeur null, `szKeyContainer` devez spécifier un conteneur valide dans le fournisseur de services de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5803e-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="5803e-109">Dans ce cas, la méthode [ICLRStrongName :: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="5803e-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="5803e-110">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="5803e-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="5803e-111">Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="5803e-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="5803e-112">Aucun autre type de clé n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="5803e-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="5803e-113">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="5803e-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="5803e-114">Cette paire est au format créé par la fonction de `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="5803e-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="5803e-115">Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `szKeyContainer` est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="5803e-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="5803e-116">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5803e-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="5803e-117">à Objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="5803e-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="5803e-118">Le paramètre `ppbPublicKeyBlob` est alloué par le common language runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5803e-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="5803e-119">L’appelant doit libérer la mémoire à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5803e-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="5803e-120">à Taille de l’objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="5803e-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5803e-121">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5803e-121">Return Value</span></span>  
 <span data-ttu-id="5803e-122">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="5803e-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5803e-123">Notes</span><span class="sxs-lookup"><span data-stu-id="5803e-123">Remarks</span></span>  
 <span data-ttu-id="5803e-124">La clé publique est contenue dans une structure [publicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="5803e-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5803e-125">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5803e-125">Requirements</span></span>  
 <span data-ttu-id="5803e-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5803e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5803e-127">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="5803e-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5803e-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5803e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5803e-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5803e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5803e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5803e-130">See also</span></span>

- [<span data-ttu-id="5803e-131">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="5803e-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="5803e-132">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="5803e-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="5803e-133">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="5803e-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
