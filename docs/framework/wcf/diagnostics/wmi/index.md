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
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Utilisation de Windows Management Instrumentation pour les diagnostics

Windows Communication Foundation (WCF) expose les données d’inspection d’un service au moment de l’exécution via un fournisseur WMI (Windows Management Instrumentation WCF).  
  
## <a name="enabling-wmi"></a>Activation de WMI  

 WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management). Pour plus d’informations sur le kit de développement logiciel (SDK) WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.  
  
 Un fournisseur WMI est un composant qui expose l'instrumentation au moment de l'exécution par l'intermédiaire d'une interface WBEM compatible. Il se compose d'un jeu d'objets WMI qui ont des paires attribut/valeur. Les paires peuvent être plusieurs types simples. Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface. WCF expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.  
  
 Le fournisseur WMI intégré peut être activé dans le fichier de configuration de l'application. Cette opération s’effectue par le biais `wmiProviderEnabled` de l’attribut de [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) dans la [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, comme indiqué dans l’exemple de configuration suivant.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Cette entrée de configuration expose une interface WMI. Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.  
  
## <a name="accessing-wmi-data"></a>Accès aux données WMI  

 Les données WMI sont accessibles de plusieurs façons différentes. Microsoft fournit des API WMI pour les scripts, les applications Visual Basic, les applications C++ et les .NET Framework. Pour plus d’informations, consultez [utilisation de WMI](/windows/win32/wmisdk/using-wmi).  
  
> [!CAUTION]
> Si vous utilisez les méthodes fournies par le .NET Framework pour accéder par programme aux données WMI, vous devez savoir que ces méthodes peuvent lever des exceptions lorsque la connexion est établie. La connexion n'est pas établie pendant la construction de l'instance <xref:System.Management.ManagementObject>, mais sur la première demande qui implique l'échange concret des données. Par conséquent, vous devez utiliser un bloc `try..catch` pour intercepter les exceptions possibles.  
  
 Vous pouvez modifier le niveau du suivi et de l'enregistrement des messages, ainsi que les options d'enregistrement des messages pour la source de suivi `System.ServiceModel` dans WMI. Pour ce faire, vous pouvez accéder à l’instance [AppDomainInfo](appdomaininfo.md) , qui expose ces propriétés booléennes : `LogMessagesAtServiceLevel` , `LogMessagesAtTransportLevel` , `LogMalformedMessages` et `TraceLevel` . Par conséquent, si vous configurez un écouteur de suivi pour l'enregistrement des messages, mais affectez la valeur `false` à ces options dans la configuration, vous pourrez leur affecter ultérieurement la valeur `true` pendant l'exécution de l'application. Ceci permet en fait d'activer l'enregistrement des messages pendant l'exécution. De la même façon, si vous activez l'enregistrement des messages dans votre fichier de configuration, vous pouvez le désactiver pendant l'exécution à l'aide de WMI.  
  
 Vous devez savoir que si aucun écouteur de suivi d'enregistrement des messages pour l'enregistrement des messages ou aucun écouteur de suivi `System.ServiceModel` pour le suivi n'est défini dans le fichier de configuration, aucune de vos modifications ne sont prises en compte, même si les modifications sont acceptées par WMI. Pour plus d’informations sur la configuration correcte des écouteurs respectifs, consultez [configuration de la journalisation des messages](../configuring-message-logging.md) et configuration du [suivi](../tracing/configuring-tracing.md). Le niveau de suivi de toutes les autres sources de suivi spécifiées par configuration est effectif lorsque l'application démarre, et ne peut pas être changé.  
  
 WCF expose une `GetOperationCounterInstanceName` méthode pour l’écriture de scripts. Cette méthode retourne un nom d'instance de compteur de performance si vous lui fournissez un nom d'opération. Toutefois, elle ne valide pas votre entrée. Par conséquent, si vous fournissez un nom d'opération erroné, un nom de compteur incorrect est retourné.  
  
 La `OutgoingChannel` propriété de l' `Service` instance ne compte pas les canaux ouverts par un service pour se connecter à un autre service, si le client WCF au service de destination n’est pas créé dans la `Service` méthode.  
  
 **Attention** WMI prend en charge uniquement une <xref:System.TimeSpan> valeur allant jusqu’à 3 points décimaux. Par exemple, si votre service affecte à l'une de ses propriétés la valeur <xref:System.TimeSpan.MaxValue>, sa valeur est tronquée après 3 virgules décimales lorsque elle est affichée dans WMI.  
  
## <a name="security"></a>Sécurité  

 Étant donné que le fournisseur WMI WCF permet la découverte de services dans un environnement, vous devez faire preuve de prudence lorsque vous accordez l’accès à celui-ci. Si vous relâchez l'accès réservé aux administrateurs par défaut, vous permettez à des correspondants d'un niveau de confiance moindre d'accéder à des données sensibles dans votre environnement. En particulier, si vous relâchez les autorisations pour l'accès WMI distant, vous risquez un grand nombre d'attaques. Si un processus est inondé par des demandes WMI excessives, cela peut nuire à ses performances.  
  
 De plus, si vous relâchez les autorisations d'accès pour le fichier MOF, les correspondants d'un niveau de confiance moindre peuvent manipuler le comportement de WMI et modifier les objets chargés dans le schéma WMI. Par exemple, des champs peuvent être supprimés au point que des données critiques sont dissimulées à l'administrateur ou que des champs qui ne se remplissent pas ou lèvent des exceptions sont ajoutés au fichier.  
  
 Par défaut, le fournisseur WMI WCF accorde l’autorisation « exécuter la méthode », « fournisseur d’écriture » et « activer le compte » pour l’administrateur et l’autorisation « activer le compte » pour ASP.NET, service local et service réseau. En particulier, sur les plateformes autres que Windows Vista, le compte ASP.NET dispose d’un accès en lecture à l’espace de noms ServiceModel WMI. Si vous ne souhaitez pas accorder ces privilèges à un groupe d'utilisateurs particulier, vous devez désactiver le fournisseur WMI (désactivé par défaut) ou désactiver l'accès pour le groupe d'utilisateurs spécifique.  
  
 De plus, lorsque vous essayez d'activer WMI par configuration, WMI peut ne pas être activé en raison de privilège utilisateur insuffisant. Toutefois, aucun événement n'est écrit dans le journal des événements pour enregistrer cette défaillance.  
  
 Pour modifier des niveaux de privilège utilisateur, utilisez les étapes suivantes.  
  
1. Cliquez sur Démarrer, puis sur Exécuter et tapez **compmgmt. msc**.  
  
2. Cliquez avec le bouton droit sur **services et applications/contrôles WMI** pour sélectionner **Propriétés**.  
  
3. Sélectionnez l’onglet **sécurité** , puis accédez à l’espace de noms **root/ServiceModel** . Cliquez sur le bouton **Sécurité**.  
  
4. Sélectionnez le groupe ou l’utilisateur spécifique pour lequel vous souhaitez contrôler l’accès et utilisez la case à cocher **autoriser** ou **refuser** pour configurer les autorisations.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Octroi d'autorisations d'inscription WCF WMI à des utilisateurs supplémentaires  

 WCF expose des données de gestion à WMI. Pour ce faire, il héberge un fournisseur WMI in-process, parfois appelé « fournisseur découplé ». Pour que les données de gestion soient exposées, le compte qui inscrit ce fournisseur doit disposer des autorisations appropriées. Dans Windows, seul un petit ensemble de comptes privilégiés peuvent inscrire des fournisseurs découplés par défaut. Cela pose problème car les utilisateurs souhaitent généralement exposer des données WMI à partir d'un service WCF s'exécutant sous un compte qui ne figure pas dans l'ensemble par défaut.  
  
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
  
     Ce script PowerShell utilise le langage SDDL (Security Descriptor Definition Language) pour accorder aux utilisateurs Built-In groupe l’accès à l’espace de noms WMI « root/ServiceModel ». Il spécifie les listes de contrôle d'accès (ACL) suivantes :  
  
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

 L'exemple de cette section octroie des privilèges d'inscription du fournisseur WMI à tous les utilisateurs locaux. Si vous souhaitez accorder l’accès à un utilisateur ou à un groupe qui n’est pas intégré, vous devez obtenir l’identificateur de sécurité (SID) de l’utilisateur ou du groupe. Il n'existe aucune méthode simple pour obtenir l'identificateur SID d'un utilisateur arbitraire. Une méthode consiste à se connecter sous le nom de l'utilisateur choisi, puis à émettre la commande shell suivante.  
  
```console
Whoami /user  
```  
  
 Ce faisant, vous obtenez l'identificateur SID de l'utilisateur actuel, mais cette méthode ne peut pas être utilisée pour obtenir le SID d'un utilisateur arbitraire. Une autre méthode pour obtenir le SID consiste à utiliser l’outil [getsid.exe](/windows/win32/wmisdk/using-wmi) à partir des outils du kit de ressources Windows 2000 pour les tâches d’administration. Cet outil compare l'identificateur SID de deux utilisateurs (locaux ou domaine), et imprime par voie de conséquence les deux SID sur la ligne de commande. Pour plus d’informations, consultez [sid connus](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Accès aux instances d'objet WMI distantes  

 Si vous avez besoin d’accéder à des instances WCF WMI sur un ordinateur distant, vous devez activer la confidentialité des paquets sur les outils que vous utilisez pour l’accès. La section suivante décrit comment y parvenir à l'aide de WMI CIM Studio, Windows Management Instrumentation Tester, et le Kit de développement .Net SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio

Si vous avez installé les outils d’administration WMI, vous pouvez utiliser WMI CIM Studio pour accéder aux instances WMI. Les outils se trouvent dans le dossier suivant :
  
*Outils Files\WMI%windir%\Program\\*
  
1. Dans la fenêtre **se connecter à l’espace de noms :** , tapez **root\ServiceModel** et cliquez sur **OK.**  
  
2. Dans la fenêtre de **connexion WMI CIM Studio** , cliquez sur le bouton **options >>** pour développer la fenêtre. Sélectionnez **confidentialité du paquet** pour **niveau d’authentification**, puis cliquez sur **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation Tester  

 Cet outil est installé par Windows. Pour l’exécuter, lancez une console de commande en tapant **cmd.exe** dans la boîte de dialogue **Démarrer/Exécuter** , puis cliquez sur **OK**. Ensuite, tapez **wbemtest.exe** dans la fenêtre de commande. Puis l'outil Windows Management Instrumentation Tester est lancé.  
  
1. Cliquez sur le bouton **se connecter** dans le coin supérieur droit de la fenêtre.  
  
2. Dans la nouvelle fenêtre, entrez **root\ServiceModel** pour le champ **espace de noms** , puis sélectionnez confidentialité du **paquet** pour **niveau d’authentification**. Cliquez sur **Connecter**.  
  
### <a name="using-managed-code"></a>Utilisation du code managé  

 Vous pouvez aussi accéder par programme aux instances WMI distantes en utilisant des classes fournies par l'espace de noms <xref:System.Management>. L'exemple de code suivant montre comment procéder.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
