---
title: 'Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460909"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="5df70-102">Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web</span><span class="sxs-lookup"><span data-stu-id="5df70-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="5df70-103">Les applications de navigateur XAML (XBAP) s’exécutent dans un bac à sable (sandbox) de sécurité de confiance partielle qui est limité au jeu d’autorisations de la zone Internet.</span><span class="sxs-lookup"><span data-stu-id="5df70-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="5df70-104">Ce jeu d’autorisations restreint les appels de service Web aux seuls services Web situés sur le site d’origine de l’application XBAP.</span><span class="sxs-lookup"><span data-stu-id="5df70-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="5df70-105">Toutefois, lorsqu’un XBAP est débogué à partir de Visual Studio 2005, il n’est pas considéré comme ayant le même site d’origine que le service Web auquel il fait référence.</span><span class="sxs-lookup"><span data-stu-id="5df70-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="5df70-106">Cela entraîne le déclenchement d’exceptions de sécurité lorsque l’application XBAP tente d’appeler le service Web.</span><span class="sxs-lookup"><span data-stu-id="5df70-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="5df70-107">Toutefois, un projet d’application de navigateur XAML (WPF) Visual Studio 2005 peut être configuré pour simuler le même site d’origine que le service Web qu’il appelle pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="5df70-107">However, a Visual Studio 2005 XAML Browser Application (WPF) project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="5df70-108">Cela permet à l’application XBAP d’appeler sans risque le service Web sans provoquer d’exceptions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5df70-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="5df70-109">Configuration de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5df70-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="5df70-110">Pour configurer Visual Studio 2005 afin de déboguer une application XBAP qui appelle un service Web :</span><span class="sxs-lookup"><span data-stu-id="5df70-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="5df70-111">Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5df70-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="5df70-112">Dans le **Concepteur de projets**, cliquez sur l’onglet **Déboguer** .</span><span class="sxs-lookup"><span data-stu-id="5df70-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="5df70-113">Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe** , puis entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df70-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="5df70-114">Dans la section **options de démarrage** , entrez ce qui suit dans la zone de texte arguments de ligne de **commande** :</span><span class="sxs-lookup"><span data-stu-id="5df70-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="5df70-115">`-debug`  *nom de fichier*</span><span class="sxs-lookup"><span data-stu-id="5df70-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="5df70-116">La valeur de *nom de fichier* pour le paramètre **-Debug** est le nom de fichier. XBAP ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="5df70-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="5df70-117">Il s’agit de la configuration par défaut pour les solutions créées avec le modèle de projet d’application de navigateur XAML (WPF) Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="5df70-117">This is the default configuration for solutions that are created with the Visual Studio 2005 XAML Browser Application (WPF) project template.</span></span>

1. <span data-ttu-id="5df70-118">Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5df70-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="5df70-119">Dans le **Concepteur de projets**, cliquez sur l’onglet **Déboguer** .</span><span class="sxs-lookup"><span data-stu-id="5df70-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="5df70-120">Dans la section **options de démarrage** , ajoutez le paramètre de ligne de commande suivant à la zone de texte arguments de ligne de **commande** :</span><span class="sxs-lookup"><span data-stu-id="5df70-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="5df70-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="5df70-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="5df70-122">La valeur de l' *URL* pour le paramètre **-DEBUGSECURITYZONEURL** est l’URL de l’emplacement que vous souhaitez simuler comme étant le site d’origine de votre application.</span><span class="sxs-lookup"><span data-stu-id="5df70-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="5df70-123">Par exemple, considérez une application de navigateur XAML (XBAP) qui utilise un service Web avec l’URL suivante :</span><span class="sxs-lookup"><span data-stu-id="5df70-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="5df70-124">L’URL du site d’origine pour ce service Web est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5df70-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="5df70-125">Par conséquent, le paramètre de ligne de commande Complete **-DebugSecurityZoneURL** et la valeur est :</span><span class="sxs-lookup"><span data-stu-id="5df70-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="5df70-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5df70-126">See also</span></span>

- [<span data-ttu-id="5df70-127">Hôte WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="5df70-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
