---
title: 'Procédure : spécifier le contexte de sécurité des services'
description: Spécifiez le contexte de sécurité pour les services. Les services exécutés dans le contexte du compte système par défaut ont d’autres droits d’accès aux ressources système que l’utilisateur connecté.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925733"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="3596f-104">Procédure : spécifier le contexte de sécurité des services</span><span class="sxs-lookup"><span data-stu-id="3596f-104">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="3596f-105">Par défaut, les services s’exécutent dans un contexte de sécurité différent de celui de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="3596f-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="3596f-106">Les services s’exécutent dans le contexte du compte système par défaut, appelé `LocalSystem`, ce qui leur confère des privilèges d’accès aux ressources système différents de ceux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3596f-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="3596f-107">Vous pouvez changer ce comportement si vous souhaitez que votre service s’exécute sous un autre compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3596f-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="3596f-108">Pour définir le contexte de sécurité, manipulez la propriété <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> du processus dans lequel le service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3596f-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="3596f-109">Cette propriété vous permet d’affecter au service l’un des quatre types de comptes suivants :</span><span class="sxs-lookup"><span data-stu-id="3596f-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="3596f-110">`User` : le système demande un nom d’utilisateur et un mot de passe valides quand le service est installé et s’exécute dans le contexte d’un compte spécifié par un utilisateur unique sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="3596f-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="3596f-111">`LocalService` : s’exécute dans le contexte d’un compte qui se comporte comme un utilisateur non privilégié sur l’ordinateur local, et présente des informations d’identification anonymes à tout serveur distant.</span><span class="sxs-lookup"><span data-stu-id="3596f-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="3596f-112">`LocalSystem` : s’exécute dans le contexte d’un compte qui fournit des privilèges locaux étendus, et présente les informations d’identification de l’ordinateur à tout serveur distant.</span><span class="sxs-lookup"><span data-stu-id="3596f-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="3596f-113">`NetworkService` : s’exécute dans le contexte d’un compte qui se comporte comme un utilisateur non privilégié sur l’ordinateur local, et présente les informations d’identification de l’ordinateur à tout serveur distant.</span><span class="sxs-lookup"><span data-stu-id="3596f-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="3596f-114">Pour plus d’informations, consultez l’énumération <xref:System.ServiceProcess.ServiceAccount>.</span><span class="sxs-lookup"><span data-stu-id="3596f-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="3596f-115">Pour spécifier le contexte de sécurité d’un service</span><span class="sxs-lookup"><span data-stu-id="3596f-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="3596f-116">Après avoir créé votre service, ajoutez les programmes d’installation nécessaires à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="3596f-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="3596f-117">Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="3596f-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="3596f-118">Dans le concepteur, accédez à la classe `ProjectInstaller`, puis cliquez sur le programme d’installation du processus de service pour le service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3596f-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3596f-119">La classe `ProjectInstaller` comprend au moins deux composants d’installation pour chaque application de service : un qui installe les processus pour tous les services dans le projet, et un programme d’installation pour chaque service contenu dans l’application.</span><span class="sxs-lookup"><span data-stu-id="3596f-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="3596f-120">Dans le cas présent, sélectionnez <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="3596f-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="3596f-121">Dans la fenêtre **Propriétés**, définissez <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> avec la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="3596f-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3596f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3596f-122">See also</span></span>

- [<span data-ttu-id="3596f-123">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="3596f-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="3596f-124">Procédure : ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="3596f-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="3596f-125">Procédure : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="3596f-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
