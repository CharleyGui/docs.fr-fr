---
title: Configuration du service de partage de ports Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: acfb720ba74cda62b2949263fcb31d356671b4f3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597512"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="c04a9-102">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="c04a9-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="c04a9-103">Les services auto-hébergés qui utilisent le transport Net.TCP peuvent contrôler plusieurs paramètres avancés, tels que `ListenBacklog` et `MaxPendingAccepts`, qui gouvernent le comportement du socket TCP sous-jacent utilisé pour la communication réseau.</span><span class="sxs-lookup"><span data-stu-id="c04a9-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="c04a9-104">Toutefois, pour chaque socket, ces paramètres ne s’appliquent qu’au niveau de la liaison si la liaison de transport a désactivé le partage de port, activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c04a9-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="c04a9-105">Lorsqu'une liaison net.tcp active le partage de port (en définissant `portSharingEnabled =true` sur l'élément de liaison de transport), elle autorise implicitement un processus externe (à savoir, l'exécutable SMSvcHost.exe, qui héberge le service de partage de ports Net.TCP) à gérer le socket TCP pour son compte.</span><span class="sxs-lookup"><span data-stu-id="c04a9-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="c04a9-106">Par exemple, lorsque vous utilisez TCP, spécifiez :</span><span class="sxs-lookup"><span data-stu-id="c04a9-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="c04a9-107">Dans le cas de cette configuration, tous les paramètres de socket spécifiés sur l’élément de liaison de transport du service sont ignorés en faveur des paramètres de socket spécifiés par SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="c04a9-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="c04a9-108">Pour configurer SMSvcHost.exe, créez un fichier de configuration XML nommé SmSvcHost.exe.config et placez-le dans le même répertoire physique que l'exécutable SMSvcHost.exe (par exemple, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="c04a9-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="c04a9-109">L'exemple suivant montre un exécutable SMSvcHost.exe.config avec les paramètres par défaut pour toutes les valeurs configurables déclarées explicitement.</span><span class="sxs-lookup"><span data-stu-id="c04a9-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="c04a9-110">Quand modifier SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="c04a9-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="c04a9-111">En général, il convient de prêter une attention particulière à la modification du contenu du fichier SMSvcHost.exe.config, parce que tout paramètre de configuration spécifié dans ce fichier affecte l'ensemble des services sur un ordinateur utilisant le service de partage de ports Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="c04a9-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="c04a9-112">Cela comprend les applications sur Windows Vista qui utilisent les fonctionnalités d’activation TCP du service d’activation des processus Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="c04a9-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="c04a9-113">Toutefois, il est parfois nécessaire de modifier la configuration par défaut du service de partage de ports Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="c04a9-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="c04a9-114">Par exemple, la valeur par défaut pour `maxPendingAccepts` est 4 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="c04a9-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="c04a9-115">Les serveurs qui hébergent un grand nombre des services utilisant le partage de port doivent augmenter cette valeur pour atteindre le débit maximal.</span><span class="sxs-lookup"><span data-stu-id="c04a9-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="c04a9-116">La valeur par défaut `maxPendingConnections` est 100.</span><span class="sxs-lookup"><span data-stu-id="c04a9-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="c04a9-117">Vous devez également envisager d’augmenter cette valeur s’il existe plusieurs clients simultanés appelant le service et le service supprime des connexions clientes.</span><span class="sxs-lookup"><span data-stu-id="c04a9-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="c04a9-118">SMSvcHost.exe.config contient également des informations concernant les identités de processus qui peuvent utiliser le service de partage de ports.</span><span class="sxs-lookup"><span data-stu-id="c04a9-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="c04a9-119">Lorsqu'un processus se connecte au service de partage de ports pour utiliser un port TCP partagé, l'identité de processus de la connexion est vérifiée dans une liste répertoriant les identités autorisées à utiliser le service.</span><span class="sxs-lookup"><span data-stu-id="c04a9-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="c04a9-120">Ces identités sont spécifiées comme identificateurs de sécurité (SID) dans la \<allowAccounts> section du fichier SMSvcHost. exe. config.</span><span class="sxs-lookup"><span data-stu-id="c04a9-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="c04a9-121">Par défaut, l'autorisation d'utiliser le service de partage de ports est accordée aux comptes système (LocalService, LocalSystem et NetworkService) ainsi qu'aux membres du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="c04a9-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="c04a9-122">Les applications qui autorisent un processus exécuté en tant qu'autre identité (par exemple, une identité de l'utilisateur) à se connecter au service de partage de ports doivent ajouter explicitement le SID approprié au fichier SMSvcHost.exe.config (ces modifications ne sont appliquées que lorsque le processus SMSvc.exe est redémarré).</span><span class="sxs-lookup"><span data-stu-id="c04a9-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c04a9-123">Sur les systèmes Windows Vista avec le contrôle de compte d’utilisateur activé, les utilisateurs locaux nécessitent des autorisations élevées, même si leur compte est membre du groupe administrateurs.</span><span class="sxs-lookup"><span data-stu-id="c04a9-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="c04a9-124">Pour permettre à ces utilisateurs d’utiliser le service de partage de port sans élévation, le SID de l’utilisateur (ou le SID d’un groupe dont l’utilisateur est membre) doit être ajouté explicitement à la \<allowAccounts> section de SMSvcHost. exe. config.</span><span class="sxs-lookup"><span data-stu-id="c04a9-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c04a9-125">Le fichier SMSvcHost.exe.config par défaut spécifie un `etwProviderId` personnalisé pour empêcher le traçage SMSvcHost.exe d'interférer avec les traces de service.</span><span class="sxs-lookup"><span data-stu-id="c04a9-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04a9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c04a9-126">See also</span></span>

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
