---
title: Nom fort (Informations de référence sur les API non managées)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7e431f3a41fadb7247f20d7ab9bb9120e827b0cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732292"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="7271d-102">Nom fort (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="7271d-102">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="7271d-103">L’API de nommage fort permet à un client d’administrer la signature avec noms forts pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="7271d-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="7271d-104">La signature d'un assembly avec un nom fort ajoute un chiffrement à clé publique au fichier contenant le manifeste d'assembly.</span><span class="sxs-lookup"><span data-stu-id="7271d-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="7271d-105">La signature avec un nom fort permet de vérifier l’unicité du nom, empêche l’usurpation de noms et fournit aux appelants une identité unique quand une référence est résolue.</span><span class="sxs-lookup"><span data-stu-id="7271d-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="7271d-106">Aucun niveau de confiance n’est toutefois associé à un nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7271d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7271d-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7271d-108">Toutes ces fonctions sont dépréciées à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="7271d-109">Pour obtenir des suggestions d’alternatives, consultez l’interface [ICLRStrongName](../hosting/iclrstrongname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7271d-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="7271d-110">GetHashFromAssemblyFile, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="7271d-111">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="7271d-112">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-113">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="7271d-114">Obtient un hachage du fichier d’assembly spécifié sous forme de chaîne Unicode, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="7271d-115">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-116">GetHashFromBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="7271d-117">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="7271d-118">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-119">GetHashFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="7271d-120">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="7271d-121">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-122">GetHashFromFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="7271d-123">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="7271d-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="7271d-124">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-125">GetHashFromHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="7271d-126">Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="7271d-127">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-128">StrongNameCompareAssemblies, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="7271d-129">Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="7271d-130">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-131">StrongNameErrorInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="7271d-132">Obtient le dernier code d’erreur déclenché par l’une des fonctions de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="7271d-133">StrongNameFreeBuffer, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="7271d-134">Libère la mémoire qui a été alloué avec un appel précédent à une fonction de nom fort comme [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) ou [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="7271d-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="7271d-135">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-136">StrongNameGetBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="7271d-137">Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7271d-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="7271d-138">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-139">StrongNameGetBlobFromImage, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="7271d-140">Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7271d-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="7271d-141">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-142">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="7271d-143">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="7271d-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="7271d-144">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-145">StrongNameHashSize, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="7271d-146">Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="7271d-147">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-148">StrongNameKeyDelete, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="7271d-149">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-149">Deletes the specified key container.</span></span> <span data-ttu-id="7271d-150">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-151">StrongNameKeyGen, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="7271d-152">Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="7271d-153">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-154">StrongNameKeyGenEx, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="7271d-155">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="7271d-156">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-157">StrongNameKeyInstall, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="7271d-158">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="7271d-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="7271d-159">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-160">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="7271d-161">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="7271d-162">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-163">StrongNameSignatureGenerationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="7271d-164">Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7271d-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="7271d-165">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-166">StrongNameSignatureSize, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="7271d-167">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="7271d-168">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-169">StrongNameSignatureVerification, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="7271d-170">Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7271d-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="7271d-171">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-172">StrongNameSignatureVerificationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="7271d-173">Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7271d-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="7271d-174">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-175">StrongNameSignatureVerificationFromImage, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="7271d-176">Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée.</span><span class="sxs-lookup"><span data-stu-id="7271d-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="7271d-177">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-178">StrongNameTokenFromAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="7271d-179">Crée un jeton de nom fort à partir du fichier d’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="7271d-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="7271d-180">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-181">StrongNameTokenFromAssemblyEx, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="7271d-182">Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique.</span><span class="sxs-lookup"><span data-stu-id="7271d-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="7271d-183">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-184">StrongNameTokenFromPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="7271d-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="7271d-185">Obtient un jeton représentant une clé publique.</span><span class="sxs-lookup"><span data-stu-id="7271d-185">Gets a token representing a public key.</span></span> <span data-ttu-id="7271d-186">Dépréciée à compter de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7271d-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="7271d-187">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="7271d-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="7271d-188">Représente la clé publique d’une paire de clés publique/privée au format binaire.</span><span class="sxs-lookup"><span data-stu-id="7271d-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7271d-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7271d-189">See also</span></span>

- [<span data-ttu-id="7271d-190">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="7271d-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="7271d-191">Informations de référence sur les API non managées</span><span class="sxs-lookup"><span data-stu-id="7271d-191">Unmanaged API Reference</span></span>](../index.md)
