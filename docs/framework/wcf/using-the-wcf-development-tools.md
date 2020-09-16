---
title: Utilisation des outils de développement WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: adaad28fee5d27976df4bf20bb54f70aec5c2daf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544620"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="442e9-102">Utilisation des outils de développement WCF</span><span class="sxs-lookup"><span data-stu-id="442e9-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="442e9-103">Cette section décrit les outils de développement Visual Studio qui peuvent vous aider à développer vos WCFservice.</span><span class="sxs-lookup"><span data-stu-id="442e9-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="442e9-104">Vous pouvez utiliser les modèles Visual Studio comme base pour créer rapidement votre propre service, puis utiliser l’hôte auto du service WCF et le client test WCF pour déboguer et tester votre service.</span><span class="sxs-lookup"><span data-stu-id="442e9-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="442e9-105">Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l'obligation de se limiter à un modèle d'hébergement à un stade précoce.</span><span class="sxs-lookup"><span data-stu-id="442e9-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="442e9-106">À compter de Visual Studio 2017, les outils de développement WCF ne sont pas installés par défaut.</span><span class="sxs-lookup"><span data-stu-id="442e9-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="442e9-107">Pour pouvoir utiliser ces fonctionnalités, vous devez vous assurer que le composant Windows Communication Foundation est sélectionné dans le programme d’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="442e9-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="442e9-108">Outils WCF Developer</span><span class="sxs-lookup"><span data-stu-id="442e9-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="442e9-109">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="442e9-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="442e9-110">Vous pouvez utiliser les modèles de projet et d’élément Visual Studio prédéfinis dans Visual Studio pour générer rapidement des services WCF et des applications environnantes.</span><span class="sxs-lookup"><span data-stu-id="442e9-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="442e9-111">Hôte de service WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="442e9-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="442e9-112">L’hôte auto du service WCF (WcfSvcHost.exe) vous permet de lancer le débogueur Visual Studio (F5) pour héberger et tester automatiquement un service que vous avez implémenté.</span><span class="sxs-lookup"><span data-stu-id="442e9-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="442e9-113">Vous pouvez ensuite tester le service à l’aide du client test WCF (wcfTestClient.exe) ou de votre propre client pour rechercher et corriger les erreurs potentielles.</span><span class="sxs-lookup"><span data-stu-id="442e9-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="442e9-114">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="442e9-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="442e9-115">Le client de test WCF (WcfTestClient.exe) est un outil d’interface graphique utilisateur qui vous permet d’entrer des paramètres de types arbitraires, d’envoyer cette entrée au service et d’afficher la réponse renvoyée par le service.</span><span class="sxs-lookup"><span data-stu-id="442e9-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="442e9-116">Il fournit une expérience de test de service transparente lorsqu’il est associé à l’hôte auto du service WCF.</span><span class="sxs-lookup"><span data-stu-id="442e9-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="442e9-117">Génération de classes de type de données à partir de XML</span><span class="sxs-lookup"><span data-stu-id="442e9-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="442e9-118">Les données XML stockées dans le presse-papiers peuvent être collées dans une page de codes.</span><span class="sxs-lookup"><span data-stu-id="442e9-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="442e9-119">Les classes définies dans les données sont converties en types de codes.</span><span class="sxs-lookup"><span data-stu-id="442e9-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="442e9-120">Utilisation des outils sans privilège d'administrateur</span><span class="sxs-lookup"><span data-stu-id="442e9-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="442e9-121">Pour permettre aux utilisateurs sans privilège d’administrateur de développer des services WCF, une liste de contrôle d’accès (ACL) (liste Access Control) est créée pour l’espace de noms « http://+:8731/Design_Time_Addresses » pendant l’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="442e9-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="442e9-122">La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="442e9-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="442e9-123">Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="442e9-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="442e9-124">Il permet également aux utilisateurs d’utiliser l’hôte auto du service WCF (wcfSvcHost.exe) sans leur accorder des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="442e9-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="442e9-125">Vous pouvez modifier l’accès à l’aide de l’outil Netsh.exe dans Windows Vista sous le compte d’administrateur avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="442e9-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="442e9-126">L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="442e9-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="442e9-127">Pour plus d’informations sur la Netsh.exe, consultez [comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commande](/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="442e9-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442e9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="442e9-128">See also</span></span>

- [<span data-ttu-id="442e9-129">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="442e9-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="442e9-130">Hôte de service WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="442e9-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="442e9-131">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="442e9-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
