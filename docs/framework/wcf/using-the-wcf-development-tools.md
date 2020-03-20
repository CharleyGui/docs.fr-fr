---
title: Utilisation des outils de développement WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183081"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="7d3e1-102">Utilisation des outils de développement WCF</span><span class="sxs-lookup"><span data-stu-id="7d3e1-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="7d3e1-103">Cette section décrit les outils de développement Visual Studio qui peuvent vous aider à développer votre service WCF.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="7d3e1-104">Vous pouvez utiliser les modèles Visual Studio comme base pour construire rapidement votre propre service, puis utiliser WCF Service Auto Host et WCF Test Client pour déboiffer et tester votre service.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="7d3e1-105">Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l'obligation de se limiter à un modèle d'hébergement à un stade précoce.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="7d3e1-106">À partir de Visual Studio 2017, les outils de développement WCF ne sont pas installés par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="7d3e1-107">Afin d’utiliser ces fonctionnalités, vous devez vous assurer que le composant De la Fondation De communication Windows est sélectionné dans l’installateur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="7d3e1-108">Outils WCF Developer</span><span class="sxs-lookup"><span data-stu-id="7d3e1-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="7d3e1-109">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="7d3e1-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="7d3e1-110">Vous pouvez utiliser le projet et les modèles d’objets Visual Studio prédéfinis dans Visual Studio pour construire rapidement les services WCF et les applications environnantes.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="7d3e1-111">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7d3e1-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="7d3e1-112">Le WCF Service Auto Host (WcfSvcHost.exe) vous permet de lancer le Visual Studio debugger (F5) pour héberger et tester automatiquement un service que vous avez mis en œuvre.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="7d3e1-113">Vous pouvez ensuite tester le service à l’aide du client de test WCF (wcfTestClient.exe) ou de votre propre client pour trouver et corriger les erreurs potentielles.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="7d3e1-114">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="7d3e1-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="7d3e1-115">WCF Test Client (WcfTestClient.exe) est un outil d’interface utilisateur qui vous permet d’entrer les paramètres des types arbitraires, de soumettre cette entrée au service et de consulter la réponse que le service renvoie.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="7d3e1-116">Il offre une expérience de test de service transparente lorsqu’il est combiné avec WCF Service Auto Host.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="7d3e1-117">Génération de classes de type de données à partir de XML</span><span class="sxs-lookup"><span data-stu-id="7d3e1-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="7d3e1-118">Les données XML stockées dans le presse-papiers peuvent être collées dans une page de codes.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="7d3e1-119">Les classes définies dans les données sont converties en types de codes.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="7d3e1-120">Utilisation des outils sans privilège d'administrateur</span><span class="sxs-lookup"><span data-stu-id="7d3e1-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="7d3e1-121">Pour permettre aux utilisateurs sans privilège d’administrateur de développer des services WCF,http://+:8731/Design_Time_Addressesun ACL (Access Control List) est créé pour le namespace " lors de l’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="7d3e1-122">La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="7d3e1-123">Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="7d3e1-124">Il permet également aux utilisateurs d’utiliser le WCF Service Auto Host (wcfSvcHost.exe) sans leur accorder de privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="7d3e1-125">Vous pouvez modifier l’accès à l’aide de l’outil Netsh.exe dans Windows Vista sous le compte administrateur élevé.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="7d3e1-126">L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7d3e1-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="7d3e1-127">Pour plus d’informations sur Netsh.exe, voir [Comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commandement](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="7d3e1-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3e1-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d3e1-128">See also</span></span>

- [<span data-ttu-id="7d3e1-129">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="7d3e1-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="7d3e1-130">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7d3e1-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="7d3e1-131">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="7d3e1-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
