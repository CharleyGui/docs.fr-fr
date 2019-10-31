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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141577"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="ad477-102">StrongNameSignatureGenerationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="ad477-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="ad477-103">Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad477-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="ad477-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="ad477-104">This function has been deprecated.</span></span> <span data-ttu-id="ad477-105">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureGenerationEx (](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ad477-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad477-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad477-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ad477-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad477-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ad477-108">dans Chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="ad477-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="ad477-109">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad477-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="ad477-110">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` devez spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="ad477-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ad477-111">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="ad477-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="ad477-112">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="ad477-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ad477-113">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad477-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ad477-114">Cette paire est au format créé par la fonction de `CryptExportKey` Win32.</span><span class="sxs-lookup"><span data-stu-id="ad477-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ad477-115">Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `wszKeyContainer` est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="ad477-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ad477-116">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ad477-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="ad477-117">à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="ad477-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="ad477-118">Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="ad477-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="ad477-119">Si `ppbSignatureBlob` n’a pas la valeur null, le common language runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="ad477-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="ad477-120">L’appelant doit libérer cet espace à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ad477-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="ad477-121">à Taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="ad477-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ad477-122">dans Une ou plusieurs des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad477-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="ad477-123">`SN_SIGN_ALL_FILES` (0x00000001)-recalcule tous les hachages pour les modules liés.</span><span class="sxs-lookup"><span data-stu-id="ad477-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="ad477-124">`SN_TEST_SIGN` (0x00000002) : testez la signature de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad477-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad477-125">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ad477-125">Return Value</span></span>  
 <span data-ttu-id="ad477-126">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ad477-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad477-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ad477-127">Remarks</span></span>  
 <span data-ttu-id="ad477-128">Spécifiez NULL pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="ad477-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="ad477-129">La signature peut être stockée directement dans le fichier ou être retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ad477-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="ad477-130">Si `SN_SIGN_ALL_FILES` est spécifié mais qu’une clé publique n’est pas incluse (les `pbKeyBlob` et `wszFilePath` sont null), les hachages des modules liés sont recalculés, mais l’assembly n’est pas resigné.</span><span class="sxs-lookup"><span data-stu-id="ad477-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="ad477-131">Si `SN_TEST_SIGN` est spécifié, l’en-tête common language runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ad477-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="ad477-132">Si la fonction `StrongNameSignatureGenerationEx` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="ad477-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad477-133">spécifications</span><span class="sxs-lookup"><span data-stu-id="ad477-133">Requirements</span></span>  
 <span data-ttu-id="ad477-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad477-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad477-135">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ad477-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ad477-136">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad477-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad477-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad477-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad477-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad477-138">See also</span></span>

- [<span data-ttu-id="ad477-139">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ad477-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="ad477-140">StrongNameSignatureGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="ad477-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="ad477-141">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ad477-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
