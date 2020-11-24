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
ms.openlocfilehash: 9fc517b081a1df48d943d03a9c3ce223a428bde7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671627"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="24024-102">Méthode ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="24024-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>

<span data-ttu-id="24024-103">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="24024-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24024-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24024-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="24024-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24024-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="24024-106">dans Chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="24024-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="24024-107">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="24024-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="24024-108">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="24024-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="24024-109">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="24024-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="24024-110">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="24024-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="24024-111">Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="24024-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="24024-112">Aucun autre type de clé n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="24024-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="24024-113">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="24024-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="24024-114">Cette paire est au format créé par la fonction Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="24024-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="24024-115">Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `wszKeyContainer` est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="24024-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="24024-116">dans Taille, en octets, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="24024-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="24024-117">à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="24024-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="24024-118">Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="24024-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="24024-119">Si `ppbSignatureBlob` n’a pas la valeur null, le Common Language Runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="24024-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="24024-120">L’appelant doit libérer cet espace à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24024-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="24024-121">à Taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="24024-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24024-122">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="24024-122">Return Value</span></span>  

 <span data-ttu-id="24024-123">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="24024-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24024-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="24024-124">Remarks</span></span>  

 <span data-ttu-id="24024-125">Spécifiez NULL pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="24024-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="24024-126">La signature peut être stockée soit directement dans le fichier, soit retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="24024-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24024-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24024-127">Requirements</span></span>  

 <span data-ttu-id="24024-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24024-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24024-129">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="24024-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="24024-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24024-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24024-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24024-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24024-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24024-132">See also</span></span>

- [<span data-ttu-id="24024-133">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="24024-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="24024-134">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="24024-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
