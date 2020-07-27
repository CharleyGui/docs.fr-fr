---
title: Cert2spc.exe (outil de test de certificat d'éditeur de logiciels)
description: Utilisez Cert2spc.exe, l’outil de test de certificat de l’éditeur de logiciels. Cet outil crée un certificat SPC (Software Publisher) à partir d’un ou de plusieurs certificats X. 509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 2eb6339aa6f5d23a5b87986410cbeaac2dac2bec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167312"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="a988f-104">Cert2spc.exe (outil de test de certificat d'éditeur de logiciels)</span><span class="sxs-lookup"><span data-stu-id="a988f-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="a988f-105">L'outil Software Publisher Certificate Test (Test de certificat d'édition de logiciel) crée un certificat d'édition de logiciel SPC (Software Publisher's Certificate) à partir d'un ou plusieurs certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="a988f-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="a988f-106">Cert2spc.exe doit être utilisé à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="a988f-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="a988f-107">Vous pouvez vous procurer un certificat SPC valide auprès d'une autorité de certification comme VeriSign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="a988f-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="a988f-108">Pour plus d’informations sur la création de certificats X.509, consultez [Makecert.exe (outil de création de certificat)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="a988f-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="a988f-109">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a988f-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a988f-110">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a988f-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a988f-111">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a988f-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a988f-112">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a988f-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a988f-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a988f-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="a988f-114">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a988f-114">Parameters</span></span>  
  
|<span data-ttu-id="a988f-115">Argument</span><span class="sxs-lookup"><span data-stu-id="a988f-115">Argument</span></span>|<span data-ttu-id="a988f-116">Description</span><span class="sxs-lookup"><span data-stu-id="a988f-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="a988f-117">Nom d'un certificat X.509 à inclure dans le fichier SPC.</span><span class="sxs-lookup"><span data-stu-id="a988f-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="a988f-118">Vous pouvez spécifier plusieurs noms séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="a988f-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="a988f-119">Nom d'une liste de révocation de certificats à inclure dans le fichier SPC.</span><span class="sxs-lookup"><span data-stu-id="a988f-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="a988f-120">Vous pouvez spécifier plusieurs noms séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="a988f-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="a988f-121">Nom de l'objet PKCS #7 qui contiendra les certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="a988f-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="a988f-122">Option</span><span class="sxs-lookup"><span data-stu-id="a988f-122">Option</span></span>|<span data-ttu-id="a988f-123">Description</span><span class="sxs-lookup"><span data-stu-id="a988f-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a988f-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="a988f-124">**/?**</span></span>|<span data-ttu-id="a988f-125">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="a988f-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="a988f-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="a988f-126">Examples</span></span>  
 <span data-ttu-id="a988f-127">La commande suivante crée un fichier SPC à partir de `myCertificate.cer` et le place dans `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="a988f-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="a988f-128">La commande suivante crée un fichier SPC à partir de `oneCertificate.cer` et `twoCertificate.cer` et le place dans `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="a988f-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="a988f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a988f-129">See also</span></span>

- [<span data-ttu-id="a988f-130">outils</span><span class="sxs-lookup"><span data-stu-id="a988f-130">Tools</span></span>](index.md)
- [<span data-ttu-id="a988f-131">Makecert.exe (outil de la création du certificat)</span><span class="sxs-lookup"><span data-stu-id="a988f-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="a988f-132">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="a988f-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
