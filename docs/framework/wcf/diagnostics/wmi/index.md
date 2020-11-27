---
title: Utilisation de Windows Management Instrumentation pour les diagnostics
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: cb015096f9e7cb815e5bd4e4e5487c03fea49bc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267934"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="d3879-102">Utilisation de Windows Management Instrumentation pour les diagnostics</span><span class="sxs-lookup"><span data-stu-id="d3879-102">Using Windows Management Instrumentation for Diagnostics</span></span>

<span data-ttu-id="d3879-103">Windows Communication Foundation (WCF) expose les données d’inspection d’un service au moment de l’exécution via un fournisseur WMI (Windows Management Instrumentation WCF).</span><span class="sxs-lookup"><span data-stu-id="d3879-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="d3879-104">Activation de WMI</span><span class="sxs-lookup"><span data-stu-id="d3879-104">Enabling WMI</span></span>  

 <span data-ttu-id="d3879-105">WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management).</span><span class="sxs-lookup"><span data-stu-id="d3879-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="d3879-106">Pour plus d’informations sur le kit de développement logiciel (SDK) WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="d3879-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="d3879-107">WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.</span><span class="sxs-lookup"><span data-stu-id="d3879-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="d3879-108">Un fournisseur WMI est un composant qui expose l'instrumentation au moment de l'exécution par l'intermédiaire d'une interface WBEM compatible.</span><span class="sxs-lookup"><span data-stu-id="d3879-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="d3879-109">Il se compose d'un jeu d'objets WMI qui ont des paires attribut/valeur.</span><span class="sxs-lookup"><span data-stu-id="d3879-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="d3879-110">Les paires peuvent être plusieurs types simples.</span><span class="sxs-lookup"><span data-stu-id="d3879-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="d3879-111">Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface.</span><span class="sxs-lookup"><span data-stu-id="d3879-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="d3879-112">WCF expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.</span><span class="sxs-lookup"><span data-stu-id="d3879-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="d3879-113">Le fournisseur WMI intégré peut être activé dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="d3879-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="d3879-114">Cette opération s’effectue par le biais `wmiProviderEnabled` de l’attribut de [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) dans la [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="d3879-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d3879-115">Cette entrée de configuration expose une interface WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="d3879-116">Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.</span><span class="sxs-lookup"><span data-stu-id="d3879-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="d3879-117">Accès aux données WMI</span><span class="sxs-lookup"><span data-stu-id="d3879-117">Accessing WMI Data</span></span>  

 <span data-ttu-id="d3879-118">Les données WMI sont accessibles de plusieurs façons différentes.</span><span class="sxs-lookup"><span data-stu-id="d3879-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="d3879-119">Microsoft fournit des API WMI pour les scripts, les applications Visual Basic, les applications C++ et les .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="d3879-120">Pour plus d’informations, consultez [utilisation de WMI](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="d3879-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d3879-121">Si vous utilisez les méthodes fournies par le .NET Framework pour accéder par programme aux données WMI, vous devez savoir que ces méthodes peuvent lever des exceptions lorsque la connexion est établie.</span><span class="sxs-lookup"><span data-stu-id="d3879-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="d3879-122">La connexion n'est pas établie pendant la construction de l'instance <xref:System.Management.ManagementObject>, mais sur la première demande qui implique l'échange concret des données.</span><span class="sxs-lookup"><span data-stu-id="d3879-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="d3879-123">Par conséquent, vous devez utiliser un bloc `try..catch` pour intercepter les exceptions possibles.</span><span class="sxs-lookup"><span data-stu-id="d3879-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="d3879-124">Vous pouvez modifier le niveau du suivi et de l'enregistrement des messages, ainsi que les options d'enregistrement des messages pour la source de suivi `System.ServiceModel` dans WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="d3879-125">Pour ce faire, vous pouvez accéder à l’instance [AppDomainInfo](appdomaininfo.md) , qui expose ces propriétés booléennes : `LogMessagesAtServiceLevel` , `LogMessagesAtTransportLevel` , `LogMalformedMessages` et `TraceLevel` .</span><span class="sxs-lookup"><span data-stu-id="d3879-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="d3879-126">Par conséquent, si vous configurez un écouteur de suivi pour l'enregistrement des messages, mais affectez la valeur `false` à ces options dans la configuration, vous pourrez leur affecter ultérieurement la valeur `true` pendant l'exécution de l'application.</span><span class="sxs-lookup"><span data-stu-id="d3879-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="d3879-127">Ceci permet en fait d'activer l'enregistrement des messages pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d3879-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="d3879-128">De la même façon, si vous activez l'enregistrement des messages dans votre fichier de configuration, vous pouvez le désactiver pendant l'exécution à l'aide de WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="d3879-129">Vous devez savoir que si aucun écouteur de suivi d'enregistrement des messages pour l'enregistrement des messages ou aucun écouteur de suivi `System.ServiceModel` pour le suivi n'est défini dans le fichier de configuration, aucune de vos modifications ne sont prises en compte, même si les modifications sont acceptées par WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="d3879-130">Pour plus d’informations sur la configuration correcte des écouteurs respectifs, consultez [configuration de la journalisation des messages](../configuring-message-logging.md) et configuration du [suivi](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="d3879-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="d3879-131">Le niveau de suivi de toutes les autres sources de suivi spécifiées par configuration est effectif lorsque l'application démarre, et ne peut pas être changé.</span><span class="sxs-lookup"><span data-stu-id="d3879-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="d3879-132">WCF expose une `GetOperationCounterInstanceName` méthode pour l’écriture de scripts.</span><span class="sxs-lookup"><span data-stu-id="d3879-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="d3879-133">Cette méthode retourne un nom d'instance de compteur de performance si vous lui fournissez un nom d'opération.</span><span class="sxs-lookup"><span data-stu-id="d3879-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="d3879-134">Toutefois, elle ne valide pas votre entrée.</span><span class="sxs-lookup"><span data-stu-id="d3879-134">However, it does not validate your input.</span></span> <span data-ttu-id="d3879-135">Par conséquent, si vous fournissez un nom d'opération erroné, un nom de compteur incorrect est retourné.</span><span class="sxs-lookup"><span data-stu-id="d3879-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="d3879-136">La `OutgoingChannel` propriété de l' `Service` instance ne compte pas les canaux ouverts par un service pour se connecter à un autre service, si le client WCF au service de destination n’est pas créé dans la `Service` méthode.</span><span class="sxs-lookup"><span data-stu-id="d3879-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="d3879-137">**Attention** WMI prend en charge uniquement une <xref:System.TimeSpan> valeur allant jusqu’à 3 points décimaux.</span><span class="sxs-lookup"><span data-stu-id="d3879-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="d3879-138">Par exemple, si votre service affecte à l'une de ses propriétés la valeur <xref:System.TimeSpan.MaxValue>, sa valeur est tronquée après 3 virgules décimales lorsque elle est affichée dans WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="d3879-139">Sécurité</span><span class="sxs-lookup"><span data-stu-id="d3879-139">Security</span></span>  

 <span data-ttu-id="d3879-140">Étant donné que le fournisseur WMI WCF permet la découverte de services dans un environnement, vous devez faire preuve de prudence lorsque vous accordez l’accès à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d3879-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="d3879-141">Si vous relâchez l'accès réservé aux administrateurs par défaut, vous permettez à des correspondants d'un niveau de confiance moindre d'accéder à des données sensibles dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="d3879-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="d3879-142">En particulier, si vous relâchez les autorisations pour l'accès WMI distant, vous risquez un grand nombre d'attaques.</span><span class="sxs-lookup"><span data-stu-id="d3879-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="d3879-143">Si un processus est inondé par des demandes WMI excessives, cela peut nuire à ses performances.</span><span class="sxs-lookup"><span data-stu-id="d3879-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="d3879-144">De plus, si vous relâchez les autorisations d'accès pour le fichier MOF, les correspondants d'un niveau de confiance moindre peuvent manipuler le comportement de WMI et modifier les objets chargés dans le schéma WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="d3879-145">Par exemple, des champs peuvent être supprimés au point que des données critiques sont dissimulées à l'administrateur ou que des champs qui ne se remplissent pas ou lèvent des exceptions sont ajoutés au fichier.</span><span class="sxs-lookup"><span data-stu-id="d3879-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="d3879-146">Par défaut, le fournisseur WMI WCF accorde l’autorisation « exécuter la méthode », « fournisseur d’écriture » et « activer le compte » pour l’administrateur et l’autorisation « activer le compte » pour ASP.NET, service local et service réseau.</span><span class="sxs-lookup"><span data-stu-id="d3879-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="d3879-147">En particulier, sur les plateformes autres que Windows Vista, le compte ASP.NET dispose d’un accès en lecture à l’espace de noms ServiceModel WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="d3879-148">Si vous ne souhaitez pas accorder ces privilèges à un groupe d'utilisateurs particulier, vous devez désactiver le fournisseur WMI (désactivé par défaut) ou désactiver l'accès pour le groupe d'utilisateurs spécifique.</span><span class="sxs-lookup"><span data-stu-id="d3879-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="d3879-149">De plus, lorsque vous essayez d'activer WMI par configuration, WMI peut ne pas être activé en raison de privilège utilisateur insuffisant.</span><span class="sxs-lookup"><span data-stu-id="d3879-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="d3879-150">Toutefois, aucun événement n'est écrit dans le journal des événements pour enregistrer cette défaillance.</span><span class="sxs-lookup"><span data-stu-id="d3879-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="d3879-151">Pour modifier des niveaux de privilège utilisateur, utilisez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="d3879-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="d3879-152">Cliquez sur Démarrer, puis sur Exécuter et tapez **compmgmt. msc**.</span><span class="sxs-lookup"><span data-stu-id="d3879-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="d3879-153">Cliquez avec le bouton droit sur **services et applications/contrôles WMI** pour sélectionner **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d3879-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="d3879-154">Sélectionnez l’onglet **sécurité** , puis accédez à l’espace de noms **root/ServiceModel** .</span><span class="sxs-lookup"><span data-stu-id="d3879-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="d3879-155">Cliquez sur le bouton **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="d3879-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="d3879-156">Sélectionnez le groupe ou l’utilisateur spécifique pour lequel vous souhaitez contrôler l’accès et utilisez la case à cocher **autoriser** ou **refuser** pour configurer les autorisations.</span><span class="sxs-lookup"><span data-stu-id="d3879-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="d3879-157">Octroi d'autorisations d'inscription WCF WMI à des utilisateurs supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d3879-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  

 <span data-ttu-id="d3879-158">WCF expose des données de gestion à WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="d3879-159">Pour ce faire, il héberge un fournisseur WMI in-process, parfois appelé « fournisseur découplé ».</span><span class="sxs-lookup"><span data-stu-id="d3879-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="d3879-160">Pour que les données de gestion soient exposées, le compte qui inscrit ce fournisseur doit disposer des autorisations appropriées.</span><span class="sxs-lookup"><span data-stu-id="d3879-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="d3879-161">Dans Windows, seul un petit ensemble de comptes privilégiés peuvent inscrire des fournisseurs découplés par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3879-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="d3879-162">Cela pose problème car les utilisateurs souhaitent généralement exposer des données WMI à partir d'un service WCF s'exécutant sous un compte qui ne figure pas dans l'ensemble par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3879-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="d3879-163">Pour fournir cet accès, un administrateur doit octroyer les autorisations suivantes au compte supplémentaire dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="d3879-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="d3879-164">Autorisation pour accéder à l'espace de noms WCF WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="d3879-165">Autorisation d'inscrire le fournisseur WMI découplé WCF.</span><span class="sxs-lookup"><span data-stu-id="d3879-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="d3879-166">Pour octroyer l'autorisation d'accès à l'espace de noms WMI</span><span class="sxs-lookup"><span data-stu-id="d3879-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="d3879-167">Exécutez le script PowerShell suivant.</span><span class="sxs-lookup"><span data-stu-id="d3879-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="d3879-168">Ce script PowerShell utilise le langage SDDL (Security Descriptor Definition Language) pour accorder aux utilisateurs Built-In groupe l’accès à l’espace de noms WMI « root/ServiceModel ».</span><span class="sxs-lookup"><span data-stu-id="d3879-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="d3879-169">Il spécifie les listes de contrôle d'accès (ACL) suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3879-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="d3879-170">Administrateurs intégrés (BA) - Bénéficie déjà d'un accès.</span><span class="sxs-lookup"><span data-stu-id="d3879-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="d3879-171">Service réseau (NS) - Bénéficie déjà d'un accès.</span><span class="sxs-lookup"><span data-stu-id="d3879-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="d3879-172">Système local (LS) - Bénéficie déjà d'un accès.</span><span class="sxs-lookup"><span data-stu-id="d3879-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="d3879-173">Utilisateurs intégrés - Groupe auquel octroyer l'accès.</span><span class="sxs-lookup"><span data-stu-id="d3879-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="d3879-174">Pour octroyer l'accès d'inscription du fournisseur</span><span class="sxs-lookup"><span data-stu-id="d3879-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="d3879-175">Exécutez le script PowerShell suivant.</span><span class="sxs-lookup"><span data-stu-id="d3879-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="d3879-176">Octroi de l'accès à des groupes ou des utilisateurs arbitraires</span><span class="sxs-lookup"><span data-stu-id="d3879-176">Granting Access to Arbitrary Users or Groups</span></span>  

 <span data-ttu-id="d3879-177">L'exemple de cette section octroie des privilèges d'inscription du fournisseur WMI à tous les utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="d3879-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="d3879-178">Si vous souhaitez accorder l’accès à un utilisateur ou à un groupe qui n’est pas intégré, vous devez obtenir l’identificateur de sécurité (SID) de l’utilisateur ou du groupe.</span><span class="sxs-lookup"><span data-stu-id="d3879-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="d3879-179">Il n'existe aucune méthode simple pour obtenir l'identificateur SID d'un utilisateur arbitraire.</span><span class="sxs-lookup"><span data-stu-id="d3879-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="d3879-180">Une méthode consiste à se connecter sous le nom de l'utilisateur choisi, puis à émettre la commande shell suivante.</span><span class="sxs-lookup"><span data-stu-id="d3879-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="d3879-181">Ce faisant, vous obtenez l'identificateur SID de l'utilisateur actuel, mais cette méthode ne peut pas être utilisée pour obtenir le SID d'un utilisateur arbitraire.</span><span class="sxs-lookup"><span data-stu-id="d3879-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="d3879-182">Une autre méthode pour obtenir le SID consiste à utiliser l’outil [getsid.exe](/windows/win32/wmisdk/using-wmi) à partir des outils du kit de ressources Windows 2000 pour les tâches d’administration.</span><span class="sxs-lookup"><span data-stu-id="d3879-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="d3879-183">Cet outil compare l'identificateur SID de deux utilisateurs (locaux ou domaine), et imprime par voie de conséquence les deux SID sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d3879-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="d3879-184">Pour plus d’informations, consultez [sid connus](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="d3879-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="d3879-185">Accès aux instances d'objet WMI distantes</span><span class="sxs-lookup"><span data-stu-id="d3879-185">Accessing Remote WMI Object Instances</span></span>  

 <span data-ttu-id="d3879-186">Si vous avez besoin d’accéder à des instances WCF WMI sur un ordinateur distant, vous devez activer la confidentialité des paquets sur les outils que vous utilisez pour l’accès.</span><span class="sxs-lookup"><span data-stu-id="d3879-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="d3879-187">La section suivante décrit comment y parvenir à l'aide de WMI CIM Studio, Windows Management Instrumentation Tester, et le Kit de développement .Net SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3879-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="d3879-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="d3879-188">WMI CIM Studio</span></span>

<span data-ttu-id="d3879-189">Si vous avez installé les outils d’administration WMI, vous pouvez utiliser WMI CIM Studio pour accéder aux instances WMI.</span><span class="sxs-lookup"><span data-stu-id="d3879-189">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="d3879-190">Les outils se trouvent dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="d3879-190">The tools are in the following folder:</span></span>
  
<span data-ttu-id="d3879-191">*Outils Files\WMI%windir%\Program\\*</span><span class="sxs-lookup"><span data-stu-id="d3879-191">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="d3879-192">Dans la fenêtre **se connecter à l’espace de noms :** , tapez **root\ServiceModel** et cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="d3879-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="d3879-193">Dans la fenêtre de **connexion WMI CIM Studio** , cliquez sur le bouton **options >>** pour développer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d3879-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="d3879-194">Sélectionnez **confidentialité du paquet** pour **niveau d’authentification**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3879-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="d3879-195">Windows Management Instrumentation Tester</span><span class="sxs-lookup"><span data-stu-id="d3879-195">Windows Management Instrumentation Tester</span></span>  

 <span data-ttu-id="d3879-196">Cet outil est installé par Windows.</span><span class="sxs-lookup"><span data-stu-id="d3879-196">This tool is installed by Windows.</span></span> <span data-ttu-id="d3879-197">Pour l’exécuter, lancez une console de commande en tapant **cmd.exe** dans la boîte de dialogue **Démarrer/Exécuter** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3879-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="d3879-198">Ensuite, tapez **wbemtest.exe** dans la fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="d3879-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="d3879-199">Puis l'outil Windows Management Instrumentation Tester est lancé.</span><span class="sxs-lookup"><span data-stu-id="d3879-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="d3879-200">Cliquez sur le bouton **se connecter** dans le coin supérieur droit de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d3879-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="d3879-201">Dans la nouvelle fenêtre, entrez **root\ServiceModel** pour le champ **espace de noms** , puis sélectionnez confidentialité du **paquet** pour **niveau d’authentification**.</span><span class="sxs-lookup"><span data-stu-id="d3879-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="d3879-202">Cliquez sur **Connecter**.</span><span class="sxs-lookup"><span data-stu-id="d3879-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="d3879-203">Utilisation du code managé</span><span class="sxs-lookup"><span data-stu-id="d3879-203">Using Managed Code</span></span>  

 <span data-ttu-id="d3879-204">Vous pouvez aussi accéder par programme aux instances WMI distantes en utilisant des classes fournies par l'espace de noms <xref:System.Management>.</span><span class="sxs-lookup"><span data-stu-id="d3879-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="d3879-205">L'exemple de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="d3879-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
