---
title: ReadMe pour l'exemple d'authentification de protection étendue
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601099"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="c579e-102">ReadMe pour l'exemple d'authentification de protection étendue</span><span class="sxs-lookup"><span data-stu-id="c579e-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="c579e-103">La protection étendue est une initiative de sécurité visant à se protéger contre les attaques de l’intercepteur (intercepteur), dans lesquelles un attaquant (le « Man-in-the-Middle ») intercepte les informations d’identification d’un client et les utilise pour accéder à des ressources sécurisées sur le serveur prévu du client.</span><span class="sxs-lookup"><span data-stu-id="c579e-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="c579e-104">Pour plus d’informations, consultez [protection étendue de l’authentification vue d’ensemble](extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c579e-104">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c579e-105">Cet exemple fonctionne uniquement dans le cadre d'un hébergement sur IIS.</span><span class="sxs-lookup"><span data-stu-id="c579e-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="c579e-106">Ile ne fonctionne pas sur Visual Studio Development Server car il ne prend pas en charge HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c579e-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c579e-107">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c579e-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="c579e-108">Installez IIS sur l’ordinateur à partir de Ajout/suppression de programmes-> fonctionnalités Windows.</span><span class="sxs-lookup"><span data-stu-id="c579e-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="c579e-109">Activer l’authentification Windows dans les fonctionnalités Windows : Internet Information Services-> World Wide Web services-> la sécurité > l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="c579e-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="c579e-110">Activer l’activation HTTP dans les fonctionnalités Windows : Microsoft .NET Framework 3.5.1-> Windows Communication Foundation l’activation HTTP.</span><span class="sxs-lookup"><span data-stu-id="c579e-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="c579e-111">Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite la présence d'un certificat de serveur qui peut être installé à partir du gestionnaire des services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="c579e-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="c579e-112">Ouvrez le gestionnaire des services Internet-> certificats de serveur (à partir de l’onglet Affichage des fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="c579e-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="c579e-113">À des fins de test de cet exemple, vous pouvez créer un certificat auto-signé.</span><span class="sxs-lookup"><span data-stu-id="c579e-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="c579e-114">(Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, vous pouvez l'installer dans la banque d'autorités racine approuvées de certificats).</span><span class="sxs-lookup"><span data-stu-id="c579e-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="c579e-115">Accédez au volet Actions pour le site web par défaut.</span><span class="sxs-lookup"><span data-stu-id="c579e-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="c579e-116">Cliquez sur modifier les liaisons de > de site.</span><span class="sxs-lookup"><span data-stu-id="c579e-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="c579e-117">Ajoutez HTTPS comme type s'il ne l'est pas encore, avec le numéro de port 443, et affectez le certificat SSL créé à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="c579e-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="c579e-118">Générez le service.</span><span class="sxs-lookup"><span data-stu-id="c579e-118">Build the service.</span></span> <span data-ttu-id="c579e-119">Un répertoire virtuel est alors créé dans IIS (à partir de l'action post-build spécifiée dans les propriétés de projet) et les fichiers dll, .svc et de configuration sont copiés comme requis pour l'hébergement d'un service sur le Web.</span><span class="sxs-lookup"><span data-stu-id="c579e-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="c579e-120">Ouvrez le gestionnaire des services IIS.</span><span class="sxs-lookup"><span data-stu-id="c579e-120">Open the IIS Manager.</span></span> <span data-ttu-id="c579e-121">Cliquez avec le bouton droit sur le répertoire virtuel (ExtendedProtection) que vous avez créé à l'étape précédente et sélectionnez Convertir en application.</span><span class="sxs-lookup"><span data-stu-id="c579e-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="c579e-122">Ouvrez le module Authentification dans le gestionnaire des services IIS de ce répertoire virtuel et activez l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="c579e-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="c579e-123">Ouvrez les paramètres avancés de l'authentification Windows pour ce répertoire virtuel et définissez la valeur Requis, car, dans cet exemple, le paramètre ExtendedProtection correspondant est défini sur Toujours.</span><span class="sxs-lookup"><span data-stu-id="c579e-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="c579e-124">Vous pouvez tester le service en accédant à l'URL depuis une fenêtre de navigateur.</span><span class="sxs-lookup"><span data-stu-id="c579e-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="c579e-125">Si vous souhaitez accéder à cette URL depuis plusieurs ordinateurs, assurez-vous que le pare-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.</span><span class="sxs-lookup"><span data-stu-id="c579e-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="c579e-126">Ouvrez le fichier de configuration client et fournissez un nom d’ordinateur complet pour l' \<client>  -  \<endpoint> attribut-address, en remplaçant \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="c579e-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="c579e-127">Exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="c579e-127">Run the client.</span></span> <span data-ttu-id="c579e-128">Le client communique avec le service en établissant un canal sécurisé et en utilisant une protection étendue de manière discrète.</span><span class="sxs-lookup"><span data-stu-id="c579e-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
