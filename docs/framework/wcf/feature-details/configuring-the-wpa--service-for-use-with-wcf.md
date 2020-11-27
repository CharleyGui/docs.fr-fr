---
title: Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 2f84afba72e5260a44726dcc812401da5475679f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284093"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="98e42-102">Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="98e42-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>

<span data-ttu-id="98e42-103">Cette rubrique décrit les étapes requises pour configurer le service d’activation des processus Windows (également appelé WAS) dans Windows Vista pour héberger des services Windows Communication Foundation (WCF) qui ne communiquent pas sur des protocoles réseau HTTP.</span><span class="sxs-lookup"><span data-stu-id="98e42-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="98e42-104">Les sections suivantes définissent les étapes pour cette configuration :</span><span class="sxs-lookup"><span data-stu-id="98e42-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="98e42-105">Installez (ou confirmez l’installation de) les composants d’activation WCF requis.</span><span class="sxs-lookup"><span data-stu-id="98e42-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="98e42-106">Créez un site WAS avec les liaisons de protocole réseau que vous souhaitez utiliser ou ajoutez un nouveau protocole qui crée une liaison vers un site existant.</span><span class="sxs-lookup"><span data-stu-id="98e42-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="98e42-107">Créez une application pour héberger vos services et permettre à cette application d'utiliser les protocoles réseau requis.</span><span class="sxs-lookup"><span data-stu-id="98e42-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="98e42-108">Générez un service WCF qui expose un point de terminaison non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="98e42-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="98e42-109">Configuration d’un site avec des liaisons non HTTP</span><span class="sxs-lookup"><span data-stu-id="98e42-109">Configuring a Site with Non-HTTP bindings</span></span>  

 <span data-ttu-id="98e42-110">Pour utiliser une liaison non HTTP avec le service WAS, la liaison de site doit être ajoutée à la configuration WAS.</span><span class="sxs-lookup"><span data-stu-id="98e42-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="98e42-111">Le magasin de configurations pour le service WAS est le fichier applicationHost.config situé dans le répertoire %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="98e42-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="98e42-112">Ce magasin de configurations est partagé à la fois par le service WAS et le service IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="98e42-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="98e42-113">applicationHost.config est un fichier texte XML qui peut être ouvert avec un éditeur de texte standard (tel que le Bloc-notes).</span><span class="sxs-lookup"><span data-stu-id="98e42-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="98e42-114">Toutefois, l’outil de configuration de ligne de commande IIS 7,0 (appcmd.exe) est la méthode recommandée pour ajouter des liaisons de site non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="98e42-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="98e42-115">La commande suivante ajoute une liaison de site net.tcp au site Web par défaut à l'aide de appcmd.exe (cette commande est entrée comme une ligne unique).</span><span class="sxs-lookup"><span data-stu-id="98e42-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="98e42-116">Cette commande ajoute la nouvelle liaison net.tcp au site web par défaut en ajoutant la ligne indiquée ci-dessous au fichier applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="98e42-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="98e42-117">Activation de l'utilisation des protocoles non HTTP par une application</span><span class="sxs-lookup"><span data-stu-id="98e42-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  

 <span data-ttu-id="98e42-118">Vous pouvez activer ou désactiver le protocolsat réseau individuel au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="98e42-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="98e42-119">La commande suivante montre comment activer à la fois les protocoles HTTP et net.tcp pour une application qui s'exécute dans le `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="98e42-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="98e42-120">La liste des Protocoles activés peut également être définie dans l' \<applicationDefaults> élément de la configuration XML du site stocké dans ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="98e42-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="98e42-121">Le code XML suivant issu du fichier applicationHost.config illustre un site lié à la fois à des protocoles HTTP et non HTTP.</span><span class="sxs-lookup"><span data-stu-id="98e42-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="98e42-122">La configuration supplémentaire requise pour la prise en charge de protocoles non HTTP est appelée avec des commentaires.</span><span class="sxs-lookup"><span data-stu-id="98e42-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="98e42-123">Si vous tentez d'activer un service en utilisant WAS pour l'activation non-HTTP et vous n'avez pas installé et configuré WAS, l'erreur suivante s'affiche :</span><span class="sxs-lookup"><span data-stu-id="98e42-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="98e42-124">Si cette erreur s'affiche, assurez-vous que WAS pour l'activation non HTTP est installé et configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="98e42-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="98e42-125">Pour plus d’informations, consultez [Comment : installer et configurer des composants d’activation WCF](how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="98e42-125">For more information, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="98e42-126">Génération d'un service WCF qui utilise le service WAS pour l'activation non HTTP</span><span class="sxs-lookup"><span data-stu-id="98e42-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  

 <span data-ttu-id="98e42-127">Une fois que vous avez effectué les étapes d’installation et de configuration de WAS (voir [Comment : installer et configurer des composants d’activation WCF](how-to-install-and-configure-wcf-activation-components.md)), la configuration d’un service pour utiliser was pour l’activation est semblable à la configuration d’un service hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="98e42-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="98e42-128">Pour obtenir des instructions détaillées sur la création d’un service WCF activé par WAS, consultez [Comment : héberger un service WCF dans was](how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="98e42-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e42-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98e42-129">See also</span></span>

- [<span data-ttu-id="98e42-130">Hébergement dans le service d'activation de processus de Windows (WAS, Windows Process Activation Service)</span><span class="sxs-lookup"><span data-stu-id="98e42-130">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="98e42-131">[Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="98e42-131">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
