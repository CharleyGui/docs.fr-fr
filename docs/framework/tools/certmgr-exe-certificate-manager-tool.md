---
title: Certmgr.exe (outil de gestionnaire de certificats)
description: Explorez Certmgr.exe, l’outil Gestionnaire de certificats. Cet outil gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: 30a35ded6fc86af6dc6dd4bf19cdf60f66570e0c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247250"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="2f73c-104">Certmgr.exe (outil de gestionnaire de certificats)</span><span class="sxs-lookup"><span data-stu-id="2f73c-104">Certmgr.exe (Certificate Manager Tool)</span></span>

<span data-ttu-id="2f73c-105">L'outil Certificate Manager (Certmgr.exe) gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).</span><span class="sxs-lookup"><span data-stu-id="2f73c-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="2f73c-106">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f73c-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2f73c-107">Pour démarrer l’outil, utilisez des [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2f73c-107">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f73c-108">L'outil Certificate Manager (Certmgr.exe) est un utilitaire en ligne de commande, alors que Certificats (Certmgr.msc) est un composant logiciel enfichable MMC (Microsoft Management Console).</span><span class="sxs-lookup"><span data-stu-id="2f73c-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="2f73c-109">Comme Certmgr.msc se trouve généralement dans le répertoire système de Windows, quand vous entrez `certmgr` sur la ligne de commande, vous pouvez charger le composant logiciel enfichable MMC Certificats même si vous avez ouvert l'invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f73c-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2f73c-110">Cela se produit parce que le chemin d’accès au composant logiciel enfichable précède le chemin d’accès à l’outil Certificate Manager dans la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="2f73c-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="2f73c-111">Si vous rencontrez ce problème, vous pouvez exécuter des commandes Certmgr.exe en spécifiant le chemin d'accès au fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="2f73c-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="2f73c-112">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f73c-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2f73c-113">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="2f73c-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2f73c-114">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2f73c-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2f73c-115">Pour une vue d'ensemble des certificats X.509, consultez [Utilisation des certificats](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2f73c-115">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="2f73c-116">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="2f73c-116">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f73c-117">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f73c-117">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f73c-118">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f73c-118">Parameters</span></span>  
  
|<span data-ttu-id="2f73c-119">Argument</span><span class="sxs-lookup"><span data-stu-id="2f73c-119">Argument</span></span>|<span data-ttu-id="2f73c-120">Description</span><span class="sxs-lookup"><span data-stu-id="2f73c-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2f73c-121">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="2f73c-121">*sourceStorename*</span></span>|<span data-ttu-id="2f73c-122">Le magasin de certificats qui contient les certificats existants, les CTL ou CRL à ajouter, supprimer, enregistrer ou afficher.</span><span class="sxs-lookup"><span data-stu-id="2f73c-122">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="2f73c-123">Il peut s'agir d'un fichier de magasin ou d'un magasin système.</span><span class="sxs-lookup"><span data-stu-id="2f73c-123">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="2f73c-124">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="2f73c-124">*destinationStorename*</span></span>|<span data-ttu-id="2f73c-125">Magasin ou fichier du certificat de sortie.</span><span class="sxs-lookup"><span data-stu-id="2f73c-125">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="2f73c-126">Option</span><span class="sxs-lookup"><span data-stu-id="2f73c-126">Option</span></span>|<span data-ttu-id="2f73c-127">Description</span><span class="sxs-lookup"><span data-stu-id="2f73c-127">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2f73c-128">**/Add**</span><span class="sxs-lookup"><span data-stu-id="2f73c-128">**/add**</span></span>|<span data-ttu-id="2f73c-129">Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-129">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="2f73c-130">**All**</span><span class="sxs-lookup"><span data-stu-id="2f73c-130">**/all**</span></span>|<span data-ttu-id="2f73c-131">Ajoute toutes les entrées si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-131">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="2f73c-132">Supprime toutes les entrées si utilisée avec **/del**. Affiche toutes les entrées quand elles sont utilisées sans les options **/Add** ou **/del** .</span><span class="sxs-lookup"><span data-stu-id="2f73c-132">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="2f73c-133">L'option **/all** ne peut pas être utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-133">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2f73c-134">**commutateur**</span><span class="sxs-lookup"><span data-stu-id="2f73c-134">**/c**</span></span>|<span data-ttu-id="2f73c-135">Ajoute des certificats si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-135">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="2f73c-136">Supprime des certificats lorsqu’il est utilisé avec **/del**. Enregistre les certificats lorsqu’ils sont utilisés avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-136">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="2f73c-137">Affiche des certificats si utilisée sans les options **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2f73c-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="2f73c-138">**/CRL**</span></span>|<span data-ttu-id="2f73c-139">Ajoute des listes de révocation de certificats si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="2f73c-140">Supprime les listes de révocation de certificats lorsqu’elles sont utilisées avec **/del**. Enregistre les listes de révocation de certificats lorsqu’elles sont utilisées avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-140">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="2f73c-141">Affiche les listes de révocation des certificats si utilisée sans les options **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-141">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2f73c-142">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="2f73c-142">**/CTL**</span></span>|<span data-ttu-id="2f73c-143">Ajoute des listes de certificats de confiance si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-143">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="2f73c-144">Supprime des listes CTL en cas d’utilisation avec **/del**. Enregistre les listes CTL en cas d’utilisation avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-144">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="2f73c-145">Affiche des listes de certificats de confiance si utilisée sans l'option **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-145">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2f73c-146">**/del**</span><span class="sxs-lookup"><span data-stu-id="2f73c-146">**/del**</span></span>|<span data-ttu-id="2f73c-147">Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-147">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="2f73c-148">**/e** *type d’encodage*</span><span class="sxs-lookup"><span data-stu-id="2f73c-148">**/e** *encodingType*</span></span>|<span data-ttu-id="2f73c-149">Spécifie le type d'encodage des certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-149">Specifies the certificate encoding type.</span></span> <span data-ttu-id="2f73c-150">La valeur par défaut est `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-150">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="2f73c-151">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="2f73c-151">**/f** *dwFlags*</span></span>|<span data-ttu-id="2f73c-152">Spécifie l'indicateur d'ouverture du magasin.</span><span class="sxs-lookup"><span data-stu-id="2f73c-152">Specifies the store open flag.</span></span> <span data-ttu-id="2f73c-153">Il s'agit du paramètre *dwFlags* passé à **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-153">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="2f73c-154">Sa valeur par défaut est CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2f73c-154">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="2f73c-155">Cette option n'est prise en compte que si l'option **/y** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f73c-155">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="2f73c-156">**/h**[**IDE**]</span><span class="sxs-lookup"><span data-stu-id="2f73c-156">**/h**[**elp**]</span></span>|<span data-ttu-id="2f73c-157">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="2f73c-157">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2f73c-158">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="2f73c-158">**/n** *nam*</span></span>|<span data-ttu-id="2f73c-159">Spécifie le nom commun du certificat à ajouter, à supprimer ou à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="2f73c-159">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="2f73c-160">Cette option ne peut être utilisée qu'avec des certificats ; elle n'est pas compatible avec les listes de certificats de confiance, ni avec les listes de révocation de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-160">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="2f73c-161">**/put**</span><span class="sxs-lookup"><span data-stu-id="2f73c-161">**/put**</span></span>|<span data-ttu-id="2f73c-162">Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-162">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="2f73c-163">Le fichier est enregistré au format X.509.</span><span class="sxs-lookup"><span data-stu-id="2f73c-163">The file is saved in X.509 format.</span></span> <span data-ttu-id="2f73c-164">Vous pouvez utiliser l'option **/7** avec l'option **/put** pour enregistrer le fichier au format PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="2f73c-164">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="2f73c-165">L'option **/put** doit être suivie par **/c**, **/CTL** ou **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-165">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="2f73c-166">L'option **/all** ne peut pas être utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-166">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2f73c-167">**/r** *emplacement*</span><span class="sxs-lookup"><span data-stu-id="2f73c-167">**/r** *location*</span></span>|<span data-ttu-id="2f73c-168">Identifie l'emplacement du magasin système dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="2f73c-168">Identifies the registry location of the system store.</span></span> <span data-ttu-id="2f73c-169">Cette option n'est prise en compte que si l'option **/s** est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f73c-169">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="2f73c-170">La valeur de *location* doit être l'une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f73c-170">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="2f73c-171">-   `currentUser` indique que le magasin de certificats se trouve sous la clé HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2f73c-171">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="2f73c-172">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f73c-172">This is the default.</span></span><br /><span data-ttu-id="2f73c-173">-   `localMachine` indique que le magasin de certificats se trouve sous la clé HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="2f73c-173">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="2f73c-174">**commutateur**</span><span class="sxs-lookup"><span data-stu-id="2f73c-174">**/s**</span></span>|<span data-ttu-id="2f73c-175">Indique que le magasin de certificats est un magasin système.</span><span class="sxs-lookup"><span data-stu-id="2f73c-175">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="2f73c-176">Si vous ne spécifiez pas cette option, le magasin est considéré comme **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-176">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="2f73c-177">**/sha1** *hachage sha1*</span><span class="sxs-lookup"><span data-stu-id="2f73c-177">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="2f73c-178">Spécifie le hachage SHA1 du certificat, de la liste de certificats de confiance ou de la liste de révocation de certificats à ajouter, à supprimer ou à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="2f73c-178">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="2f73c-179">**/v**</span><span class="sxs-lookup"><span data-stu-id="2f73c-179">**/v**</span></span>|<span data-ttu-id="2f73c-180">Spécifie le mode Commentaires ; affiche des informations détaillées sur les certificats, les listes de certificats de confiance et les listes de révocation de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-180">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="2f73c-181">Vous ne pouvez pas utiliser cette option avec **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2f73c-181">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="2f73c-182">**/y** *fournisseur*</span><span class="sxs-lookup"><span data-stu-id="2f73c-182">**/y** *provider*</span></span>|<span data-ttu-id="2f73c-183">Spécifie le nom du fournisseur de magasin.</span><span class="sxs-lookup"><span data-stu-id="2f73c-183">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="2f73c-184">**/7**</span><span class="sxs-lookup"><span data-stu-id="2f73c-184">**/7**</span></span>|<span data-ttu-id="2f73c-185">Enregistre le magasin de destination comme un objet PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="2f73c-185">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="2f73c-186">**/?**</span><span class="sxs-lookup"><span data-stu-id="2f73c-186">**/?**</span></span>|<span data-ttu-id="2f73c-187">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="2f73c-187">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f73c-188">Notes</span><span class="sxs-lookup"><span data-stu-id="2f73c-188">Remarks</span></span>  

 <span data-ttu-id="2f73c-189">Certmgr.exe exécute les fonctions de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f73c-189">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="2f73c-190">Affiche les certificats, listes de certificats de confiance et listes de révocation de certificats dans la console.</span><span class="sxs-lookup"><span data-stu-id="2f73c-190">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="2f73c-191">Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-191">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="2f73c-192">Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-192">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="2f73c-193">Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-193">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="2f73c-194">Certmgr.exe fonctionne avec deux types de magasins de certificats : **StoreFile** et magasin système.</span><span class="sxs-lookup"><span data-stu-id="2f73c-194">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="2f73c-195">Il n'est pas nécessaire de spécifier le type de magasin de certificats ; Certmgr.exe est capable de l'identifier et d'effectuer les opérations appropriées.</span><span class="sxs-lookup"><span data-stu-id="2f73c-195">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="2f73c-196">L'exécution de Certmgr.exe sans aucune option lance le composant logiciel enfichable certmgr.msc, qui dispose d'une interface utilisateur graphique (GUI) qui facilite les tâches de gestion des certificats qui sont également disponibles à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2f73c-196">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="2f73c-197">Cette interface utilisateur graphique fournit un Assistant d'importation qui copie les certificats, les listes de certificats de confiance et les listes de révocation de certificats depuis votre disque vers un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2f73c-197">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="2f73c-198">Vous pouvez rechercher les noms de magasins de certificats X509 pour les paramètres `sourceStorename` et `destinationStorename` en compilant et en exécutant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2f73c-198">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="2f73c-199">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2f73c-199">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2f73c-200">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f73c-200">Examples</span></span>  

 <span data-ttu-id="2f73c-201">La commande suivante affiche un magasin système par défaut appelé `my` avec une sortie des commentaires.</span><span class="sxs-lookup"><span data-stu-id="2f73c-201">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="2f73c-202">La commande suivante ajoute tous les certificats contenus dans un fichier nommé `myFile.ext` dans un nouveau fichier appelé `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-202">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="2f73c-203">La commande suivante ajoute le certificat dans un fichier nommé `testcert.cer` au magasin système `my`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-203">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="2f73c-204">La commande suivante ajoute le certificat dans un fichier nommé `TrustedCert.cer` dans le magasin de certificats racines.</span><span class="sxs-lookup"><span data-stu-id="2f73c-204">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="2f73c-205">La commande suivante enregistre un certificat avec le nom commun `myCert` dans le magasin système `my` vers un fichier nommé `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-205">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="2f73c-206">La commande suivante supprime toutes les listes de certificats de confiance du magasin système `my` et enregistre le magasin qui en résulte dans un fichier nommé `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-206">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="2f73c-207">La commande suivante enregistre un certificat dans le magasin système `my` du fichier `newFile`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-207">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="2f73c-208">Vous devez saisir le numéro du certificat de `my` à placer dans `newFile`.</span><span class="sxs-lookup"><span data-stu-id="2f73c-208">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f73c-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f73c-209">See also</span></span>

- [<span data-ttu-id="2f73c-210">outils</span><span class="sxs-lookup"><span data-stu-id="2f73c-210">Tools</span></span>](index.md)
- [<span data-ttu-id="2f73c-211">Makecert.exe (outil de la création du certificat)</span><span class="sxs-lookup"><span data-stu-id="2f73c-211">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="2f73c-212">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="2f73c-212">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
