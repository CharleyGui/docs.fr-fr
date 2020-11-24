---
title: Méthode ICLRStrongName::StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 78cc043953e6288df136b43590831569d112afef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674513"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="99907-102">Méthode ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="99907-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>

<span data-ttu-id="99907-103">Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="99907-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99907-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99907-104">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99907-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99907-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="99907-106">dans Chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="99907-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="99907-107">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="99907-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="99907-108">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="99907-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="99907-109">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="99907-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="99907-110">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="99907-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="99907-111">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="99907-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="99907-112">Cette paire est au format créé par la fonction Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="99907-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="99907-113">Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `wszKeyContainer` est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="99907-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="99907-114">dans Taille, en octets, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="99907-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="99907-115">à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="99907-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="99907-116">Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="99907-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="99907-117">Si `ppbSignatureBlob` n’a pas la valeur null, le Common Language Runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="99907-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="99907-118">L’appelant doit libérer cet espace à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99907-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="99907-119">à Taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="99907-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="99907-120">dans Une ou plusieurs des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="99907-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="99907-121">`SN_SIGN_ALL_FILES` (0x00000001)-recalcule tous les hachages pour les modules liés.</span><span class="sxs-lookup"><span data-stu-id="99907-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="99907-122">`SN_TEST_SIGN` (0x00000002) : testez la signature de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="99907-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99907-123">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="99907-123">Return Value</span></span>  

 <span data-ttu-id="99907-124">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="99907-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99907-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="99907-125">Remarks</span></span>  

 <span data-ttu-id="99907-126">Spécifiez NULL pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="99907-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="99907-127">La signature peut être stockée directement dans le fichier ou être retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="99907-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="99907-128">Si `SN_SIGN_ALL_FILES` est spécifié mais qu’une clé publique n’est pas incluse ( `pbKeyBlob` et que `wszFilePath` la valeur est null), les hachages des modules liés sont recalculés, mais l’assembly n’est pas à nouveau signé.</span><span class="sxs-lookup"><span data-stu-id="99907-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="99907-129">Si `SN_TEST_SIGN` est spécifié, l’en-tête Common Language Runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="99907-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99907-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="99907-130">Requirements</span></span>  

 <span data-ttu-id="99907-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99907-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99907-132">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="99907-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99907-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99907-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99907-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99907-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99907-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99907-135">See also</span></span>

- [<span data-ttu-id="99907-136">StrongNameSignatureGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="99907-136">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="99907-137">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="99907-137">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
