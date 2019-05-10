---
title: StrongNameSignatureGenerationEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059dadcaf7a55074e30c59873a8c1e7016b0a33e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666004"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="d948c-102">StrongNameSignatureGenerationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="d948c-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="d948c-103">Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d948c-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="d948c-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="d948c-104">This function has been deprecated.</span></span> <span data-ttu-id="d948c-105">Utilisez le [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="d948c-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d948c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d948c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d948c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d948c-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d948c-108">[in] Le chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort est générée.</span><span class="sxs-lookup"><span data-stu-id="d948c-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="d948c-109">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="d948c-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="d948c-110">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="d948c-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="d948c-111">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="d948c-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="d948c-112">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="d948c-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d948c-113">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="d948c-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d948c-114">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="d948c-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d948c-115">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `wszKeyContainer` est supposée pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="d948c-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d948c-116">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d948c-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="d948c-117">[out] Pointeur vers l’emplacement auquel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="d948c-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="d948c-118">Si `ppbSignatureBlob` est null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="d948c-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="d948c-119">Si `ppbSignatureBlob` est non null, le common language runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="d948c-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="d948c-120">L’appelant doit libérer cet espace à l’aide de la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="d948c-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="d948c-121">[out] La taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="d948c-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d948c-122">[in] Un ou plusieurs des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="d948c-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="d948c-123">`SN_SIGN_ALL_FILES` (0 x 00000001) - recalculez tous les hachages pour les modules liés.</span><span class="sxs-lookup"><span data-stu-id="d948c-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="d948c-124">`SN_TEST_SIGN` (0 x 00000002) - test-signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d948c-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d948c-125">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d948c-125">Return Value</span></span>  
 <span data-ttu-id="d948c-126">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d948c-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d948c-127">Notes</span><span class="sxs-lookup"><span data-stu-id="d948c-127">Remarks</span></span>  
 <span data-ttu-id="d948c-128">Spécifiez null pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="d948c-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="d948c-129">La signature peut être stockée directement dans le fichier, ou retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d948c-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="d948c-130">Si `SN_SIGN_ALL_FILES` est spécifié, mais une clé publique n’est pas incluse (les deux `pbKeyBlob` et `wszFilePath` ont la valeur null), les hachages pour les modules liés sont recalculés, mais l’assembly n’est pas signé de nouveau.</span><span class="sxs-lookup"><span data-stu-id="d948c-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="d948c-131">Si `SN_TEST_SIGN` est spécifié, l’en-tête du common language runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="d948c-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="d948c-132">Si le `StrongNameSignatureGenerationEx` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="d948c-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d948c-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d948c-133">Requirements</span></span>  
 <span data-ttu-id="d948c-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d948c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d948c-135">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d948c-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d948c-136">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d948c-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d948c-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d948c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d948c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d948c-138">See also</span></span>

- [<span data-ttu-id="d948c-139">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="d948c-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="d948c-140">StrongNameSignatureGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="d948c-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="d948c-141">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="d948c-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
