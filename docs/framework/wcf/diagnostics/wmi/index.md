---
title: Utilisation de Windows Management Instrumentation pour les diagnostics
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: ecc5c754a51a8e1a52797dfd0af0891704eaad1f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591243"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Utilisation de Windows Management Instrumentation pour les diagnostics
Windows Communication Foundation (WCF) expose des données d’inspection d’un service lors de l’exécution via un fournisseur de services WCF Windows Management Instrumentation (WMI).  
  
## <a name="enabling-wmi"></a>Activation de WMI  
 WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management). Pour plus d’informations sur le SDK WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.  
  
 Un fournisseur WMI est un composant qui expose l'instrumentation au moment de l'exécution par l'intermédiaire d'une interface WBEM compatible. Il se compose d'un jeu d'objets WMI qui ont des paires attribut/valeur. Les paires peuvent être plusieurs types simples. Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface. WCF expose des attributs de services tels que les adresses, liaisons, comportements et écouteurs.  
  
 Le fournisseur WMI intégré peut être activé dans le fichier de configuration de l'application. Cette opération est effectuée via le `wmiProviderEnabled` attribut de la [ \<diagnostics >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) dans le [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, comme illustré dans l’exemple suivant configuration.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Cette entrée de configuration expose une interface WMI. Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.  
  
## <a name="accessing-wmi-data"></a>Accès aux données WMI  
 Les données WMI sont accessibles de plusieurs façons différentes. Microsoft fournit des API WMI pour les scripts, les applications Visual Basic, C++ applications et le .NET Framework. Pour plus d’informations, consultez [à l’aide de WMI](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Si vous utilisez les méthodes fournies par le .NET Framework pour accéder par programme aux données WMI, vous devez savoir que ces méthodes peuvent lever des exceptions lorsque la connexion est établie. La connexion n'est pas établie pendant la construction de l'instance <xref:System.Management.ManagementObject>, mais sur la première demande qui implique l'échange concret des données. Par conséquent, vous devez utiliser un bloc `try..catch` pour intercepter les exceptions possibles.  
  
 Vous pouvez modifier le niveau du suivi et de l'enregistrement des messages, ainsi que les options d'enregistrement des messages pour la source de suivi `System.ServiceModel` dans WMI. Cela est possible en accédant à la [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, ce qui expose ces propriétés booléennes : `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, et `TraceLevel`. Par conséquent, si vous configurez un écouteur de suivi pour l'enregistrement des messages, mais affectez la valeur `false` à ces options dans la configuration, vous pourrez leur affecter ultérieurement la valeur `true` pendant l'exécution de l'application. Ceci permet en fait d'activer l'enregistrement des messages pendant l'exécution. De la même façon, si vous activez l'enregistrement des messages dans votre fichier de configuration, vous pouvez le désactiver pendant l'exécution à l'aide de WMI.  
  
 Vous devez savoir que si aucun écouteur de suivi d'enregistrement des messages pour l'enregistrement des messages ou aucun écouteur de suivi `System.ServiceModel` pour le suivi n'est défini dans le fichier de configuration, aucune de vos modifications ne sont prises en compte, même si les modifications sont acceptées par WMI. Pour plus d’informations sur la configuration correcte des écouteurs respectifs, consultez [configuration de la journalisation du Message](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) et [configuration du suivi](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Le niveau de suivi de toutes les autres sources de suivi spécifiées par configuration est effectif lorsque l'application démarre, et ne peut pas être changé.  
  
 WCF expose un `GetOperationCounterInstanceName` méthode pour le script. Cette méthode retourne un nom d'instance de compteur de performance si vous lui fournissez un nom d'opération. Toutefois, elle ne valide pas votre entrée. Par conséquent, si vous fournissez un nom d'opération erroné, un nom de compteur incorrect est retourné.  
  
 Le `OutgoingChannel` propriété de la `Service` instance ne compte pas les canaux ouverts par un service pour se connecter à un autre service, si le client WCF au service de destination n’est pas créé dans le `Service` (méthode).  
  
 **Attention** WMI prend uniquement en charge un <xref:System.TimeSpan> valeur jusqu'à 3 virgules décimales. Par exemple, si votre service affecte à l'une de ses propriétés la valeur <xref:System.TimeSpan.MaxValue>, sa valeur est tronquée après 3 virgules décimales lorsque elle est affichée dans WMI.  
  
## <a name="security"></a>Sécurité  
 Car le fournisseur WMI WCF permet la découverte de services dans un environnement, vous devez être très prudent avant d’accorder l’accès à celui-ci. Si vous relâchez l'accès réservé aux administrateurs par défaut, vous permettez à des correspondants d'un niveau de confiance moindre d'accéder à des données sensibles dans votre environnement. En particulier, si vous relâchez les autorisations pour l'accès WMI distant, vous risquez un grand nombre d'attaques. Si un processus est inondé par des demandes WMI excessives, cela peut nuire à ses performances.  
  
 De plus, si vous relâchez les autorisations d'accès pour le fichier MOF, les correspondants d'un niveau de confiance moindre peuvent manipuler le comportement de WMI et modifier les objets chargés dans le schéma WMI. Par exemple, des champs peuvent être supprimés au point que des données critiques sont dissimulées à l'administrateur ou que des champs qui ne se remplissent pas ou lèvent des exceptions sont ajoutés au fichier.  
  
 Par défaut, le fournisseur WMI WCF accorde « execute method », « provider write » et « enable account » pour l’administrateur et « enable account » pour ASP.NET, Service Local et Service réseau. En particulier, sur les plateformes non [!INCLUDE[wv](../../../../../includes/wv-md.md)], le compte ASP.NET a accès en lecture à l'espace de noms WMI ServiceModel. Si vous ne souhaitez pas accorder ces privilèges à un groupe d'utilisateurs particulier, vous devez désactiver le fournisseur WMI (désactivé par défaut) ou désactiver l'accès pour le groupe d'utilisateurs spécifique.  
  
 De plus, lorsque vous essayez d'activer WMI par configuration, WMI peut ne pas être activé en raison de privilège utilisateur insuffisant. Toutefois, aucun événement n'est écrit dans le journal des événements pour enregistrer cette défaillance.  
  
 Pour modifier des niveaux de privilège utilisateur, utilisez les étapes suivantes.  
  
1. Cliquez sur Démarrer puis sur Exécuter et tapez **compmgmt.msc**.  
  
2. Avec le bouton droit **Services et applications/contrôle WMI** pour sélectionner **propriétés**.  
  
3. Sélectionnez le **sécurité** onglet et accédez à la **Root/ServiceModel** espace de noms. Cliquez sur le **sécurité** bouton.  
  
4. Sélectionnez le groupe ou utilisateur spécifique que vous souhaitez contrôler l’accès et utiliser le **autoriser** ou **Deny** case à cocher pour configurer les autorisations.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Octroi d'autorisations d'inscription WCF WMI à des utilisateurs supplémentaires  
 WCF expose des données de gestion à WMI. Il le fait en hébergeant un fournisseur WMI in-process, parfois appelé « fournisseur découplé ». Pour que les données de gestion soient exposées, le compte qui inscrit ce fournisseur doit disposer des autorisations appropriées. Dans Windows, seul un petit ensemble de comptes privilégiés peuvent inscrire des fournisseurs découplés par défaut. Cela pose problème car les utilisateurs souhaitent généralement exposer des données WMI à partir d'un service WCF s'exécutant sous un compte qui ne figure pas dans l'ensemble par défaut.  
  
 Pour fournir cet accès, un administrateur doit octroyer les autorisations suivantes au compte supplémentaire dans l'ordre suivant :  
  
1. Autorisation pour accéder à l'espace de noms WCF WMI.  
  
2. Autorisation d'inscrire le fournisseur WMI découplé WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Pour octroyer l'autorisation d'accès à l'espace de noms WMI  
  
1. Exécutez le script PowerShell suivant.  
  
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
  
     Ce script PowerShell utilise la définition de langage SDDL (Security Descriptor) pour accorder l’accès de groupe d’utilisateurs intégrés à l’espace de noms WMI « root/servicemodel ». Il spécifie les listes de contrôle d'accès (ACL) suivantes :  
  
    - Administrateurs intégrés (BA) - Bénéficie déjà d'un accès.  
  
    - Service réseau (NS) - Bénéficie déjà d'un accès.  
  
    - Système local (LS) - Bénéficie déjà d'un accès.  
  
    - Utilisateurs intégrés - Groupe auquel octroyer l'accès.  
  
#### <a name="to-grant-provider-registration-access"></a>Pour octroyer l'accès d'inscription du fournisseur  
  
1. Exécutez le script PowerShell suivant.  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Octroi de l'accès à des groupes ou des utilisateurs arbitraires  
 L'exemple de cette section octroie des privilèges d'inscription du fournisseur WMI à tous les utilisateurs locaux. Si vous souhaitez octroyer l'accès à un utilisateur ou à un groupe qui n'est pas intégré, vous devez obtenir l'identificateur de sécurité (SID) de cet utilisateur ou de ce groupe. Il n'existe aucune méthode simple pour obtenir l'identificateur SID d'un utilisateur arbitraire. Une méthode consiste à se connecter sous le nom de l'utilisateur choisi, puis à émettre la commande shell suivante.  
  
```  
Whoami /user  
```  
  
 Ce faisant, vous obtenez l'identificateur SID de l'utilisateur actuel, mais cette méthode ne peut pas être utilisée pour obtenir le SID d'un utilisateur arbitraire. Une autre méthode pour obtenir le SID consiste à utiliser le [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) outil à partir de la [Windows 2000 Resource Kit Tools pour les tâches administratives](https://go.microsoft.com/fwlink/?LinkId=178660). Cet outil compare l'identificateur SID de deux utilisateurs (locaux ou domaine), et imprime par voie de conséquence les deux SID sur la ligne de commande. Pour plus d’informations, consultez [WKT SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Accès aux instances d'objet WMI distantes  
 Si vous avez besoin accéder aux instances WMI WCF sur un ordinateur distant, vous devez activer la confidentialité du paquet sur les outils que vous utilisez pour l’accès. La section suivante décrit comment y parvenir à l'aide de WMI CIM Studio, Windows Management Instrumentation Tester, et le Kit de développement .Net SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Si vous avez installé [les outils d’administration WMI](https://go.microsoft.com/fwlink/?LinkId=95185), vous pouvez utiliser WMI CIM Studio pour accéder aux instances WMI. Les outils sont dans le dossier suivant  
  
 **Outils de Files\WMI %windir%\Program\\**  
  
1. Dans le **se connecter à l’espace de noms :** fenêtre, tapez **root\ServiceModel** et cliquez sur **OK.**  
  
2. Dans le **WMI CIM Studio Login** fenêtre, cliquez sur le **Options >>** bouton pour développer la fenêtre. Sélectionnez **confidentialité du paquet** pour **niveau d’authentification**, puis cliquez sur **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation Tester  
 Cet outil est installé par Windows. Pour l’exécuter, lancez une console de commande en tapant **cmd.exe** dans le **démarrer/exécuter** boîte de dialogue et cliquez sur **OK**. Ensuite, tapez **wbemtest.exe** dans la fenêtre de commande. Puis l'outil Windows Management Instrumentation Tester est lancé.  
  
1. Cliquez sur le **Connect** bouton dans l’angle supérieur droit de la fenêtre.  
  
2. Dans la nouvelle fenêtre, entrez **root\ServiceModel** pour le **Namespace** champ, puis sélectionnez **confidentialité du paquet** pour **niveau d’authentification**. Cliquez sur **Connexion**.  
  
### <a name="using-managed-code"></a>Utilisation du code managé  
 Vous pouvez aussi accéder par programme aux instances WMI distantes en utilisant des classes fournies par l'espace de noms <xref:System.Management>. L'exemple de code suivant montre comment procéder.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
