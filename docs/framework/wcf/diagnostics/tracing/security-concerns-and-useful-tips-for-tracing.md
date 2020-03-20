---
title: Problèmes de sécurité et conseils utiles pour le suivi
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185720"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="89109-102">Problèmes de sécurité et conseils utiles pour le suivi</span><span class="sxs-lookup"><span data-stu-id="89109-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="89109-103">Cette rubrique décrit comment empêcher l'exposition des informations sensibles et fournit également des conseils utiles en cas d'utilisation de WebHost.</span><span class="sxs-lookup"><span data-stu-id="89109-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="89109-104">Utilisation d'un écouteur de suivi personnalisé avec WebHost</span><span class="sxs-lookup"><span data-stu-id="89109-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="89109-105">Si vous écrivez votre propre écouteur de suivi, vous devez savoir que les traces peuvent être perdues dans le cas d'un service hébergé sur le Web.</span><span class="sxs-lookup"><span data-stu-id="89109-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="89109-106">Lorsque WebHost recycle, il arrête le processus en cours pendant qu'un doublon prend la relève.</span><span class="sxs-lookup"><span data-stu-id="89109-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="89109-107">Toutefois, les deux processus doivent encore avoir accès à la même ressource pendant quelques temps, ce qui dépend du type d'écouteur.</span><span class="sxs-lookup"><span data-stu-id="89109-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="89109-108">Dans ce cas, `XmlWriterTraceListener` crée un fichier de suivi pour le deuxième processus, alors que le suivi des événements Windows gère plusieurs processus dans la même session et donne accès au même fichier.</span><span class="sxs-lookup"><span data-stu-id="89109-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="89109-109">Si votre propre écouteur ne fournit pas de fonctionnalités semblables, des traces peuvent être perdues lorsque le fichier est verrouillé par les deux processus.</span><span class="sxs-lookup"><span data-stu-id="89109-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="89109-110">Vous devez également savoir qu'un écouteur de suivi personnalisé peut envoyer des traces et des messages sur le câble, par exemple à une base de données distante.</span><span class="sxs-lookup"><span data-stu-id="89109-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="89109-111">En tant que responsable du déploiement d'applications, vous devez configurer les écouteurs personnalisés avec un contrôle d'accès approprié.</span><span class="sxs-lookup"><span data-stu-id="89109-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="89109-112">Vous devez également appliquer un contrôle de sécurité sur toute information personnelle qui peut être exposée à l'emplacement distant.</span><span class="sxs-lookup"><span data-stu-id="89109-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="89109-113">Enregistrement des informations sensibles</span><span class="sxs-lookup"><span data-stu-id="89109-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="89109-114">Les suivis contiennent des en-têtes de messages lorsqu'un message est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="89109-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="89109-115">Lorsque le suivi est activé, les informations personnelles dans les en-têtes spécifiques à l'application, telles qu'une chaîne de requête, et les informations de corps, telles qu'un numéro de carte de crédit, peuvent devenir visibles dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="89109-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="89109-116">Le responsable du déploiement d'applications est chargé de mettre en vigueur le contrôle d'accès sur les fichiers de configuration et de suivi.</span><span class="sxs-lookup"><span data-stu-id="89109-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="89109-117">Si vous ne souhaitez pas que ce type d'informations soit visible, vous devez désactiver le suivi ou éliminer une partie des données par filtrage si vous souhaitez partager les journaux de suivi.</span><span class="sxs-lookup"><span data-stu-id="89109-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="89109-118">Les conseils suivants peuvent vous aider à empêcher que le contenu d'un fichier de suivi ne soit exposé involontairement :</span><span class="sxs-lookup"><span data-stu-id="89109-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="89109-119">Assurez-vous que les fichiers journaux sont protégés par des listes de contrôle d'accès dans les scénarios WebHost et à auto-hébergement.</span><span class="sxs-lookup"><span data-stu-id="89109-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="89109-120">Choisissez une extension de fichier qui ne peut pas être facilement fournie à l’aide d’une demande Web.</span><span class="sxs-lookup"><span data-stu-id="89109-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="89109-121">Par exemple, l’extension de fichier .xml n’est pas un choix sûr.</span><span class="sxs-lookup"><span data-stu-id="89109-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="89109-122">Vous pouvez vérifier le guide d’administration des services Internet (IIS) pour obtenir une liste des extensions qui peuvent être servies.</span><span class="sxs-lookup"><span data-stu-id="89109-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="89109-123">Spécifiez un chemin d’accès absolu pour l’emplacement de fichier journal, qui doit être en dehors du répertoire public vroot WebHost afin d’empêcher qu’il soit accessible par un correspondant externe à l’aide d’un navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="89109-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="89109-124">Par défaut, les clés et informations personnelles, telles que le nom d'utilisateur et le mot de passe, ne sont pas enregistrées dans les traces et les messages consignés.</span><span class="sxs-lookup"><span data-stu-id="89109-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="89109-125">Toutefois, un administrateur d'ordinateur peut utiliser l'attribut `enableLoggingKnownPII` dans l'élément `machineSettings` du fichier Machine.config pour autoriser des applications qui s'exécutent sur l'ordinateur à enregistrer des informations d'identification personnelle PII (Personally Identifiable Information) connues comme suit :</span><span class="sxs-lookup"><span data-stu-id="89109-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="89109-126">Un responsable du déploiement d'applications peut ensuite utiliser l'attribut `logKnownPii` dans le fichier App.config ou Web.config pour activer la journalisation PII comme suit :</span><span class="sxs-lookup"><span data-stu-id="89109-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="89109-127">La journalisation PII est uniquement activée lorsque les deux paramètres ont la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="89109-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="89109-128">La combinaison de deux commutateurs offre la souplesse nécessaire pour enregistrer les informations personnelles connues pour chaque application.</span><span class="sxs-lookup"><span data-stu-id="89109-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="89109-129">Sachez que si vous spécifiez plusieurs sources personnalisées dans un fichier de configuration, seuls les attributs de la première sont lus.</span><span class="sxs-lookup"><span data-stu-id="89109-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="89109-130">Les autres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="89109-130">The others are ignored.</span></span> <span data-ttu-id="89109-131">Cela signifie que, pour le fichier App.config suivant, les informations personnelles ne sont pas enregistrées pour les deux sources même si la journalisation PII est explicitement activée pour la deuxième source.</span><span class="sxs-lookup"><span data-stu-id="89109-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="89109-132">Si l'élément `<machineSettings enableLoggingKnownPii="Boolean"/>` existe en dehors du fichier Machine.config, le système lève un <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="89109-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="89109-133">Les modifications ne sont effectives qu'au démarrage ou redémarrage de l'application.</span><span class="sxs-lookup"><span data-stu-id="89109-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="89109-134">Un événement est enregistré au démarrage lorsque les deux attributs ont la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="89109-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="89109-135">Un événement est également enregistré si `logKnownPii` a la valeur `true` mais que `enableLoggingKnownPii` a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="89109-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="89109-136">Pour plus d’informations sur l’exploitation forestière des IIP, consultez [l’échantillon de verrouillage de sécurité piI.](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)</span><span class="sxs-lookup"><span data-stu-id="89109-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="89109-137">L'administrateur d'ordinateur et le responsable du déploiement d'applications doivent observer la plus grande prudence lorsqu'ils utilisent ces deux commutateurs.</span><span class="sxs-lookup"><span data-stu-id="89109-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="89109-138">Si la journalisation PII est activée, les clés de sécurité et les informations personnelles sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="89109-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="89109-139">Si elle est désactivée, les données sensibles et spécifiques aux applications sont toujours enregistrées dans les corps et en-têtes des messages.</span><span class="sxs-lookup"><span data-stu-id="89109-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="89109-140">Pour une discussion plus approfondie sur la vie privée et la protection de l’IPI contre l’exposition, voir [la confidentialité des utilisateurs](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="89109-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="89109-141">De plus, l'adresse IP de l'expéditeur du message est enregistrée une fois par connexion pour les transports orientés connexion, et une fois par message envoyé par d'autres transports.</span><span class="sxs-lookup"><span data-stu-id="89109-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="89109-142">Cette opération est effectuée sans le consentement de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="89109-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="89109-143">Toutefois, cet enregistrement se produit uniquement aux niveaux de suivi Information ou Verbose, qui ne sont pas les niveaux de suivi par défaut ou recommandés dans les environnements de production, hormis pour le débogage en direct.</span><span class="sxs-lookup"><span data-stu-id="89109-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89109-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89109-144">See also</span></span>

- [<span data-ttu-id="89109-145">Traçage</span><span class="sxs-lookup"><span data-stu-id="89109-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
