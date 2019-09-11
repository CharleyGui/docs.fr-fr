---
title: Cert2spc.exe (outil de test de certificat d'éditeur de logiciels)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49a5ad951c47100199c93d03efb07ffc6fda5080
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851416"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="50f8f-102">Cert2spc.exe (outil de test de certificat d'éditeur de logiciels)</span><span class="sxs-lookup"><span data-stu-id="50f8f-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="50f8f-103">L'outil Software Publisher Certificate Test (Test de certificat d'édition de logiciel) crée un certificat d'édition de logiciel SPC (Software Publisher's Certificate) à partir d'un ou plusieurs certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="50f8f-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="50f8f-104">Cert2spc.exe doit être utilisé à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="50f8f-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="50f8f-105">Vous pouvez vous procurer un certificat SPC valide auprès d'une autorité de certification comme VeriSign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="50f8f-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="50f8f-106">Pour plus d’informations sur la création de certificats X.509, consultez [Makecert.exe (outil de création de certificat)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="50f8f-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="50f8f-107">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50f8f-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="50f8f-108">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="50f8f-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="50f8f-109">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="50f8f-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="50f8f-110">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="50f8f-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f8f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50f8f-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="50f8f-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50f8f-112">Parameters</span></span>  
  
|<span data-ttu-id="50f8f-113">Argument</span><span class="sxs-lookup"><span data-stu-id="50f8f-113">Argument</span></span>|<span data-ttu-id="50f8f-114">Description</span><span class="sxs-lookup"><span data-stu-id="50f8f-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="50f8f-115">Nom d'un certificat X.509 à inclure dans le fichier SPC.</span><span class="sxs-lookup"><span data-stu-id="50f8f-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="50f8f-116">Vous pouvez spécifier plusieurs noms séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="50f8f-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="50f8f-117">Nom d'une liste de révocation de certificats à inclure dans le fichier SPC.</span><span class="sxs-lookup"><span data-stu-id="50f8f-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="50f8f-118">Vous pouvez spécifier plusieurs noms séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="50f8f-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="50f8f-119">Nom de l'objet PKCS #7 qui contiendra les certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="50f8f-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="50f8f-120">Option</span><span class="sxs-lookup"><span data-stu-id="50f8f-120">Option</span></span>|<span data-ttu-id="50f8f-121">Description</span><span class="sxs-lookup"><span data-stu-id="50f8f-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50f8f-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="50f8f-122">**/?**</span></span>|<span data-ttu-id="50f8f-123">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="50f8f-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="50f8f-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="50f8f-124">Examples</span></span>  
 <span data-ttu-id="50f8f-125">La commande suivante crée un fichier SPC à partir de `myCertificate.cer` et le place dans `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="50f8f-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="50f8f-126">La commande suivante crée un fichier SPC à partir de `oneCertificate.cer` et `twoCertificate.cer` et le place dans `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="50f8f-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="50f8f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f8f-127">See also</span></span>

- [<span data-ttu-id="50f8f-128">Outils</span><span class="sxs-lookup"><span data-stu-id="50f8f-128">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="50f8f-129">Makecert.exe (outil de création du certificat)</span><span class="sxs-lookup"><span data-stu-id="50f8f-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="50f8f-130">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="50f8f-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
