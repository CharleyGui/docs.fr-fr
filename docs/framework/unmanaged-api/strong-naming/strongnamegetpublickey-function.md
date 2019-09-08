---
title: StrongNameGetPublicKey, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799061"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="9091a-102">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="9091a-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="9091a-103">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9091a-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="9091a-104">La paire de clés peut être fournie en tant que nom de conteneur de clé dans un fournisseur de services de chiffrement (CSP) ou en tant que collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="9091a-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="9091a-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="9091a-105">This function has been deprecated.</span></span> <span data-ttu-id="9091a-106">Utilisez la méthode [ICLRStrongName :: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="9091a-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9091a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9091a-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9091a-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9091a-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="9091a-109">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9091a-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="9091a-110">Si `pbKeyBlob` a la valeur `szKeyContainer` null, doit spécifier un conteneur valide dans le CSP.</span><span class="sxs-lookup"><span data-stu-id="9091a-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="9091a-111">Dans ce cas, `StrongNameGetPublicKey` extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="9091a-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="9091a-112">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="9091a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9091a-113">Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="9091a-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9091a-114">Aucun autre type de clé n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="9091a-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9091a-115">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9091a-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9091a-116">Cette paire est au format créé par la fonction Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="9091a-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9091a-117">Si `pbKeyBlob` a la valeur null, le conteneur de `szKeyContainer` clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="9091a-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9091a-118">dans Taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9091a-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9091a-119">à Objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="9091a-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="9091a-120">Le `ppbPublicKeyBlob` paramètre est alloué par le Common Language Runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="9091a-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="9091a-121">L’appelant doit libérer la mémoire à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9091a-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9091a-122">à Taille de l’objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="9091a-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9091a-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9091a-123">Return Value</span></span>  
 <span data-ttu-id="9091a-124">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="9091a-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9091a-125">Notes</span><span class="sxs-lookup"><span data-stu-id="9091a-125">Remarks</span></span>  
 <span data-ttu-id="9091a-126">La clé publique est contenue dans une structure [publicKeyBlob](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="9091a-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="9091a-127">Si la `StrongNameGetPublicKey` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="9091a-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9091a-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9091a-128">Requirements</span></span>  
 <span data-ttu-id="9091a-129">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9091a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9091a-130">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9091a-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9091a-131">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9091a-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9091a-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9091a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9091a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9091a-133">See also</span></span>

- [<span data-ttu-id="9091a-134">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="9091a-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="9091a-135">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="9091a-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="9091a-136">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="9091a-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="9091a-137">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="9091a-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
