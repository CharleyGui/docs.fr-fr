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
ms.openlocfilehash: 8cc28d9ccd40c65d225a96b269562c9d3dfa2124
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729887"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="9d979-102">StrongNameGetPublicKeyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="9d979-102">StrongNameGetPublicKeyEx Method</span></span>

<span data-ttu-id="9d979-103">Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.</span><span class="sxs-lookup"><span data-stu-id="9d979-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d979-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d979-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9d979-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d979-105">Parameters</span></span>  

 `pwzKeyContainer`  
 <span data-ttu-id="9d979-106">dans Nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9d979-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="9d979-107">Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="9d979-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9d979-108">Dans ce cas, la `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="9d979-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="9d979-109">Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.</span><span class="sxs-lookup"><span data-stu-id="9d979-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9d979-110">Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="9d979-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9d979-111">Aucun autre type de clé n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="9d979-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9d979-112">dans Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9d979-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9d979-113">Cette paire est au format créé par la fonction Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="9d979-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9d979-114">Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `szKeyContainer` est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="9d979-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9d979-115">dans Taille, en octets, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9d979-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9d979-116">à Objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="9d979-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="9d979-117">Le `ppbPublicKeyBlob` paramètre est alloué par le Common Language Runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="9d979-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="9d979-118">L’appelant doit libérer la mémoire à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d979-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9d979-119">à Taille de l’objet BLOB de clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="9d979-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="9d979-120">dans Algorithme de hachage de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d979-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="9d979-121">Consultez la section Notes pour obtenir la liste des valeurs acceptées.</span><span class="sxs-lookup"><span data-stu-id="9d979-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="9d979-122">dans Réservé à une utilisation ultérieure ; la valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="9d979-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d979-123">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9d979-123">Return Value</span></span>  

 <span data-ttu-id="9d979-124">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="9d979-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d979-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d979-125">Remarks</span></span>  

 <span data-ttu-id="9d979-126">La clé publique est contenue dans une structure [publicKeyBlob](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="9d979-126">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d979-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d979-127">Remarks</span></span>  

 <span data-ttu-id="9d979-128">Le tableau suivant présente l’ensemble des valeurs acceptées pour le `uHashAlgId` paramètre.</span><span class="sxs-lookup"><span data-stu-id="9d979-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="9d979-129">Nom</span><span class="sxs-lookup"><span data-stu-id="9d979-129">Name</span></span>|<span data-ttu-id="9d979-130">Value</span><span class="sxs-lookup"><span data-stu-id="9d979-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="9d979-131">None</span><span class="sxs-lookup"><span data-stu-id="9d979-131">None</span></span>|<span data-ttu-id="9d979-132">0</span><span class="sxs-lookup"><span data-stu-id="9d979-132">0</span></span>|  
|<span data-ttu-id="9d979-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="9d979-133">SHA-1</span></span>|<span data-ttu-id="9d979-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="9d979-134">0x8004</span></span>|  
|<span data-ttu-id="9d979-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="9d979-135">SHA-256</span></span>|<span data-ttu-id="9d979-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="9d979-136">0x800c</span></span>|  
|<span data-ttu-id="9d979-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="9d979-137">SHA-384</span></span>|<span data-ttu-id="9d979-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="9d979-138">0x800d</span></span>|  
|<span data-ttu-id="9d979-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="9d979-139">SHA-512</span></span>|<span data-ttu-id="9d979-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="9d979-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d979-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d979-141">Requirements</span></span>  

 <span data-ttu-id="9d979-142">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d979-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d979-143">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="9d979-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d979-144">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d979-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d979-145">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d979-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d979-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d979-146">See also</span></span>

- [<span data-ttu-id="9d979-147">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="9d979-147">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="9d979-148">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="9d979-148">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="9d979-149">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="9d979-149">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="9d979-150">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="9d979-150">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
