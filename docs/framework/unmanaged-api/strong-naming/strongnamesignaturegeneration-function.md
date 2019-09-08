---
title: StrongNameSignatureGeneration, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798968"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="ba69a-102">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="ba69a-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="ba69a-103">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="ba69a-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="ba69a-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-104">This function has been deprecated.</span></span> <span data-ttu-id="ba69a-105">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ba69a-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba69a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba69a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba69a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba69a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ba69a-108">dans Chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="ba69a-109">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="ba69a-110">Si `pbKeyBlob` a la valeur `wszKeyContainer` null, doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="ba69a-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ba69a-111">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="ba69a-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="ba69a-112">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="ba69a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ba69a-113">Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="ba69a-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ba69a-114">Aucun autre type de clé n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ba69a-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ba69a-115">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ba69a-116">Cette paire est au format créé par la fonction Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="ba69a-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ba69a-117">Si `pbKeyBlob` a la valeur null, le conteneur de `wszKeyContainer` clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="ba69a-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ba69a-118">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ba69a-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="ba69a-119">à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="ba69a-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="ba69a-120">Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le `wszFilePath`fichier spécifié par.</span><span class="sxs-lookup"><span data-stu-id="ba69a-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="ba69a-121">Si `ppbSignatureBlob` n’a pas la valeur null, le Common Language Runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="ba69a-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="ba69a-122">L’appelant doit libérer cet espace à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ba69a-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="ba69a-123">à Taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba69a-124">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ba69a-124">Return Value</span></span>  
 <span data-ttu-id="ba69a-125">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ba69a-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba69a-126">Notes</span><span class="sxs-lookup"><span data-stu-id="ba69a-126">Remarks</span></span>  
 <span data-ttu-id="ba69a-127">Spécifiez NULL `wszFilePath` pour pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="ba69a-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="ba69a-128">La signature peut être stockée soit directement dans le fichier, soit retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ba69a-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="ba69a-129">Si la `StrongNameSignatureGeneration` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="ba69a-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba69a-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ba69a-130">Requirements</span></span>  
 <span data-ttu-id="ba69a-131">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba69a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba69a-132">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ba69a-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ba69a-133">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba69a-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba69a-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba69a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba69a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba69a-135">See also</span></span>

- [<span data-ttu-id="ba69a-136">StrongNameSignatureGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="ba69a-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="ba69a-137">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ba69a-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="ba69a-138">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ba69a-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
