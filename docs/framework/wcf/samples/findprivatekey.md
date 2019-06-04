---
title: Exemple de FindPrivateKey - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490774"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="89528-102">Exemple de FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="89528-102">FindPrivateKey sample</span></span>

<span data-ttu-id="89528-103">Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="89528-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="89528-104">L'outil FindPrivateKey.exe facilite ce processus.</span><span class="sxs-lookup"><span data-stu-id="89528-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89528-105">FindPrivateKey est un exemple qui doit être compilé avant son utilisation.</span><span class="sxs-lookup"><span data-stu-id="89528-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="89528-106">Consultez le [pour générer le projet FindPrivateKey](#to-build-the-findprivatekey-project) section pour obtenir des instructions sur la création de l’outil FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="89528-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="89528-107">Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89528-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="89528-108">Toutefois, le certificat peut être consulté par un service en cours d’exécution sous un compte différent.</span><span class="sxs-lookup"><span data-stu-id="89528-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="89528-109">Par exemple, le compte de SERVICE réseau.</span><span class="sxs-lookup"><span data-stu-id="89528-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="89528-110">Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine.</span><span class="sxs-lookup"><span data-stu-id="89528-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="89528-111">L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné.</span><span class="sxs-lookup"><span data-stu-id="89528-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="89528-112">Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.</span><span class="sxs-lookup"><span data-stu-id="89528-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="89528-113">Les exemples qui utilisent des certificats pour la sécurité utilisent l’outil FindPrivateKey dans le *Setup.bat* fichier.</span><span class="sxs-lookup"><span data-stu-id="89528-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="89528-114">Une fois que le fichier de clé privée a été trouvé, vous pouvez utiliser d’autres outils tels que *Cacls.exe* pour définir les droits d’accès appropriés sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="89528-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="89528-115">Lors de l’exécution d’un service Windows Communication Foundation (WCF) sous un compte d’utilisateur, par exemple un fichier exécutable auto-hébergé, vérifiez que le compte d’utilisateur a accès en lecture seule au fichier.</span><span class="sxs-lookup"><span data-stu-id="89528-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="89528-116">Lors de l’exécution d’un service WCF sous Internet Information Services (IIS) les comptes par défaut le service sous lequel s’exécute sont le SERVICE réseau sur IIS 7 et versions antérieures, ou identité de Pool d’applications sous IIS 7.5 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="89528-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="89528-117">Pour plus d’informations, consultez [identités du Pool d’applications](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="89528-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="89528-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="89528-118">Examples</span></span>

<span data-ttu-id="89528-119">Lorsque vous accédez à un certificat pour lequel le processus n’a pas les privilèges Lire, affiche un message d’exception semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="89528-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="89528-120">Lorsque cela se produit, utilisez l’outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d’accès pour le processus que le service s’exécute sous.</span><span class="sxs-lookup"><span data-stu-id="89528-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="89528-121">Par exemple, cela est possible avec l’outil Cacls.exe comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="89528-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="89528-122">Pour générer le projet FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="89528-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="89528-123">Pour télécharger le projet, visitez [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="89528-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="89528-124">Ouvrez l’Explorateur de fichiers et accédez à la *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* dossier sous l’emplacement du répertoire où vous avez installé l’exemple.</span><span class="sxs-lookup"><span data-stu-id="89528-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="89528-125">Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89528-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="89528-126">Dans le **Build** menu, sélectionnez **régénérer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="89528-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="89528-127">Génération de la solution génère le fichier : FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="89528-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="89528-128">Conventions, les entrées de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="89528-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="89528-129">« [*option*] » représente un jeu facultatif de paramètres.</span><span class="sxs-lookup"><span data-stu-id="89528-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="89528-130">« {*option*} » représente un jeu obligatoire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="89528-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="89528-131">«*option1* &#124; *option2*» représente un choix entre plusieurs jeux d’options.</span><span class="sxs-lookup"><span data-stu-id="89528-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="89528-132">«\<*valeur*> » représente une valeur de paramètre doit être entré.</span><span class="sxs-lookup"><span data-stu-id="89528-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="89528-133">Utilisation</span><span class="sxs-lookup"><span data-stu-id="89528-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="89528-134">Où :</span><span class="sxs-lookup"><span data-stu-id="89528-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="89528-135">Si aucun paramètre est spécifié à l’invite de commande, ce texte d’aide s’affiche.</span><span class="sxs-lookup"><span data-stu-id="89528-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="89528-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="89528-136">Examples</span></span>

<span data-ttu-id="89528-137">Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », dans le magasin personnel de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="89528-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="89528-138">Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », dans le profil personnel et stocker de l’utilisateur actuel et le chemin d’accès complet du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="89528-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="89528-139">Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89528-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
