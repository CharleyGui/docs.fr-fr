---
title: Démarrage rapide de la résolution des problèmes WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: d1cae7ad2ac0fdf963d11911484b1bd534cbc129
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094733"
---
# <a name="wcf-troubleshooting-quickstart"></a>Démarrage rapide de la résolution des problèmes WCF
Cette rubrique décrit quelques problèmes connus rencontrés par les clients lorsqu'ils développement des clients et services WCF. Si le problème que vous rencontrez n'est pas répertorié dans la liste, nous vous recommandons de configurer le traçage de votre service. Vous allez ainsi générer un fichier de suivi que vous pourrez consulter à l'aide de la visionneuse dédiée pour obtenir des informations détaillées sur les exceptions pouvant se produire au sein du service. Pour plus d’informations sur la configuration du traçage, consultez [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md). Pour plus d’informations sur la visionneuse de fichier de traçage, consultez [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Après l'installation de Windows 7 et IIS, lorsque vous tentez d'accéder à un service WCF, vous obtenez le message d'erreur suivant : Erreur HTTP 404.3 –Introuvable](#bkmk_0)  
  
     Erreur HTTP 404.3 – Introuvable. Impossible d’afficher la page demandée en raison de la configuration d’extension. Si la page est un script, ajoutez un gestionnaire. Si le fichier doit être téléchargé, ajoutez un mappage MIME. Erreur détaillée InformationModule StaticFileModule.  
  
2. [Je reçois parfois un MessageSecurityException sur la deuxième demande si mon client est inactif pendant un certain temps après la première demande. Que se passe-t-il?](#BKMK_q1)  
  
3. [Mon service commence à rejeter les nouveaux clients une fois qu’environ 10 clients interagissent avec lui. Que se passe-t-il?](#BKMK_q2)  
  
4. [Est-ce que je peux charger la configuration de mon service autrement qu'à partir du fichier de configuration de l'application WCF ?](#BKMK_q3)  
  
5. [Mon service et mon client fonctionnent très bien, mais je ne parviens pas à les faire fonctionner lorsque le client se trouve sur un autre ordinateur ? Que se passe-t-il?](#BKMK_q4)  
  
6. [Lorsque je lève une exception FaultException\<> où le type est une exception, je reçois toujours un type FaultException général sur le client et non le type générique. Que se passe-t-il?](#BKMK_q5)  
  
7. [Il semble que les opérations à sens unique et demande-réponse renvoient à peu près la même vitesse lorsque la réponse ne contient pas de données. Que se passe-t-il?](#BKMK_q6)  
  
8. [J’utilise un certificat X. 509 avec mon service et j’obtiens System. Security. Cryptography. CryptographicException. Que se passe-t-il?](#BKMK_q77)  
  
9. [J’ai remplacé les majuscules du premier paramètre d’une opération par des minuscules ; désormais, mon client lève une exception. Que se passe-t-il?](#BKMK_q88)  
  
10. [J’utilise l’un de mes outils de suivi et j’obtiens un EndpointNotFoundException. Que se passe-t-il?](#BKMK_q99)  
  
11. [Lors de l'appel d'une application HTTP Web WCF à partir d'une application SOAP WCF, le service retourne l'erreur suivante : 405 Méthode non autorisée](#BK_MK99)  
  
 [Qu’est-ce que l’adresse de base ? Comment est-elle liée à une adresse de point de terminaison ?](#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Après l'installation de Windows 7 et IIS, lorsque vous tentez d'accéder à un service WCF, vous obtenez le message d'erreur suivant : Erreur HTTP 404.3 –Introuvable  
 Voici le message d'erreur complet :  
  
 Erreur HTTP 404.3 – Introuvable. Impossible d’afficher la page demandée en raison de la configuration d’extension. Si la page est un script, ajoutez un gestionnaire. Si le fichier doit être téléchargé, ajoutez un mappage MIME. Erreur détaillée InformationModule StaticFileModule.  
  
 Ce message d’erreur s’affiche lorsque « Windows Communication Foundation HTTP activation » n’est pas défini explicitement dans le panneau de configuration. Pour ce faire, accédez au panneau de configuration, puis cliquez sur programmes dans le coin inférieur gauche de la fenêtre. Cliquez sur Activer ou désactiver des fonctionnalités Windows. Développez l'élément Microsoft .NET Framework 3.5.1, puis sélectionnez Activation HTTP de Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Je reçois parfois une MessageSecurityException sur la deuxième demande si mon client est inactif pendant un instant après la première demande. Ce qui se passe  
 La deuxième demande peut échouer pour deux raisons principales : (1) la session a expiré ou (2) le serveur Web qui héberge le service est recyclé. Dans le premier cas, la session est valide jusqu’à ce que le service expire. Lorsque le service ne reçoit pas de demande du client pendant la période spécifiée dans la liaison du service (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), le service met fin à la session de sécurité. Les messages clients suivants engendrent une <xref:System.ServiceModel.Security.MessageSecurityException>. Le client doit de nouveau établir une session sécurisée avec le service pour envoyer de futurs messages ou utiliser un jeton de contexte de sécurité avec état. Les jetons de contexte de sécurité avec état permettent également à une session sécurisée de survivre à un serveur Web en cours de recyclage. Pour plus d’informations sur l’utilisation des jetons de contexte sécurisé avec état dans une session sécurisée, consultez [Comment : créer un jeton de contexte de sécurité pour une session sécurisée](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Vous pouvez également désactiver des sessions sécurisées. Lorsque vous utilisez la liaison [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) , vous pouvez définir la propriété `establishSecurityContext` sur `false` pour désactiver les sessions sécurisées. Pour désactiver des sessions sécurisées pour d'autres liaisons, vous devez créer une liaison personnalisée. Pour plus d’informations sur la création d’une liaison personnalisée, consultez [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Avant d'appliquer chacune de ces options, vous devez comprendre les conditions de sécurité de votre application.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Mon service commence à rejeter les nouveaux clients une fois qu'environ 10 clients interagissent avec lui. Ce qui se passe  
 Par défaut, les services peuvent avoir uniquement 10 sessions simultanées. Par conséquent, si les liaisons de service utilisent des sessions, le service accepte les nouvelles connexions clientes jusqu'à ce qu'il atteigne ce nombre, après quoi il refuse les nouvelles connexions clientes jusqu'à ce que l'une des sessions en cours se termine. Vous pouvez prendre en charge davantage de clients de plusieurs manières. Si votre service ne requiert pas de sessions, n’utilisez pas de liaison avec session. (Pour plus d’informations, consultez [utilisation de sessions](using-sessions.md).) Une autre option consiste à augmenter la limite de session en remplaçant la valeur de la propriété <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> par le nombre approprié à votre situation.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Est-ce que je peux charger la configuration de mon service autrement qu'à partir du fichier de configuration de l'application WCF ?  
 Oui. Toutefois vous devez créer une classe <xref:System.ServiceModel.ServiceHost> personnalisée qui remplace la méthode <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> . À l'intérieur de cette méthode, vous pouvez appeler la base pour charger la configuration en premier (si vous souhaitez charger également les informations de configuration standard), mais vous pouvez également remplacer entièrement le système de chargement de la configuration. Si vous souhaitez charger la configuration à partir d’un fichier de configuration différent du fichier de configuration de l’application, vous devez analyser le fichier de configuration vous-même et charger la configuration.  
  
 L'exemple de code suivant indique la manière de substituer la méthode <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> et de configurer directement un point de terminaison.  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Mon service et mon client fonctionnent convenablement, mais je ne parviens pas à les faire fonctionner lorsque le client est sur un autre ordinateur. Que se passe-t-il ?  
 En fonction de l'exception, plusieurs problèmes peuvent exister :  
  
- Vous devrez peut-être remplacer les adresses de point de terminaison du client par le nom d'hôte, au lieu de « localhost ».  
  
- Vous devrez peut-être ouvrir le port vers l'application. Pour plus d’informations, consultez [Firewall Instructions](./samples/firewall-instructions.md) dans les exemples du Kit de développement logiciel.  
  
- Pour d’autres problèmes possibles, consultez la rubrique Exemples [exécution des exemples de Windows Communication Foundation](./samples/running-the-samples.md).  
  
- Si votre client utilise des informations d'identification Windows et que l'exception est une <xref:System.ServiceModel.Security.SecurityNegotiationException>, configurez Kerberos comme suit.  
  
    1. Ajoutez les informations d'identification à l'élément de point de terminaison dans le fichier App.config du client :  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. Exécutez le service auto-hébergé sous le compte System ou NetworkService. Vous pouvez exécuter cette commande pour créer une fenêtre de commande sous le compte System :  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hébergez le service sous IIS (Internet Information Services) qui, par défaut, utilise le compte du nom de principal du service (SPN).  
  
    4. Enregistrez un nouveau SPN avec le domaine à l'aide de SetSPN. Pour ce faire, vous devez être administrateur de domaine.  
  
 Pour plus d’informations sur le protocole Kerberos, consultez [concepts de sécurité utilisés dans WCF](./feature-details/security-concepts-used-in-wcf.md) et :  
  
- [Débogage d’erreurs d’authentification Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Inscription de noms de principaux du service Kerberos à l’aide de Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Kerberos Explained (Présentation de Kerberos)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Lorsque je lève une exception FaultException\<> où le type est une exception, je reçois toujours un type FaultException général sur le client et non le type générique. Que se passe-t-il ?  
 Il est fortement recommandé de créer votre propre type de données d'erreur personnalisé et de le déclarer comme le type de détail dans votre contrat d'erreur. La raison est que l'utilisation des types d'exceptions fournis par le système :  
  
- crée une dépendance des types qui supprime l'une des plus grandes forces des applications orientées service ;  
  
- ne peut pas dépendre d'exceptions sérialisant de manière standard (certaines, comme <xref:System.Security.SecurityException>risquent de pas être du tout sérialisables) ;  
  
- expose des informations d'implémentation interne aux clients. Pour plus d’informations, consultez [spécification et gestion des erreurs dans les contrats et les services](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Si vous déboguez une application, toutefois, vous pouvez sérialiser des informations sur les exceptions et les renvoyer au client à l'aide de la classe <xref:System.ServiceModel.Description.ServiceDebugBehavior> .  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Il semble que les opérations monodirectionnelles et demande-réponse reviennent quasiment à la même vitesse lorsque la réponse ne contient pas de données. Que se passe-t-il ?  
 Spécifier qu'une opération est monodirectionnelle signifie uniquement que le contrat de l'opération accepte un message d'entrée et ne renvoie pas de message de sortie. Dans WCF, tous les appels clients sont retournés lorsque les données sortantes ont été écrites sur le câble ou qu’une exception est levée. Les opérations monodirectionnelles fonctionnent de la même façon et elles peuvent lever si le service ne peut pas être localisé ou bloquer si le service n'est pas préparé à accepter les données du réseau. En général, dans WCF, les appels unidirectionnels sont retournés au client plus rapidement qu’une demande-réponse ; Toutefois, toute condition qui ralentit l’envoi des données sortantes sur le réseau ralentit les opérations monodirectionnelles, ainsi que les opérations de demande-réponse. Pour plus d’informations, consultez [services unidirectionnels](./feature-details/one-way-services.md) et [accès aux services à l’aide d’un client WCF](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>J'utilise un certificat X.509 avec mon service et j'obtiens une System.Security.Cryptography.CryptographicException. Que se passe-t-il ?  
 Cela se produit couramment après avoir modifié le compte d'utilisateur sous lequel le processus de travail IIS s'exécute. Par exemple, dans Windows XP, si vous modifiez le compte d’utilisateur par défaut sous lequel le Aspnet_wp. exe s’exécute à partir de ASPNET en un compte d’utilisateur personnalisé, vous pouvez voir cette erreur. Lors de l'utilisation d'une clé privée, le processus qui l'utilise aura besoin des autorisations d'accès au fichier qui stocke cette clé.  
  
 Le cas échéant, vous devez octroyer des privilèges d'accès en lecture au compte du processus pour le fichier contenant la clé privée. Par exemple, si le processus de travail IIS s'exécute sous le compte Jacques, vous devrez octroyer à Jacques un accès en lecture au fichier contenant la clé privée.  
  
 Pour plus d’informations sur la façon d’octroyer au compte d’utilisateur un accès au fichier qui contient la clé privée pour un certificat X. 509 spécifique, consultez [Comment : rendre des certificats x. 509 accessibles à WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>J'ai remplacé les majuscules du premier paramètre d'une opération par des minuscules ; à présent, mon client lève une exception. Que se passe-t-il ?  
 Les valeurs des noms de paramètres dans la signature d’opération font partie du contrat et respectent la casse. Utilisez l'attribut <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> lorsque vous devez distinguer le nom du paramètre local et les métadonnées qui décrivent l'opération pour les applications clientes.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>J'utilise l'un de mes outils de suivi et j'obtiens une EndpointNotFoundException. Que se passe-t-il ?  
 Si vous utilisez un outil de suivi qui n’est pas le mécanisme de suivi WCF fourni par le système et que vous recevez une <xref:System.ServiceModel.EndpointNotFoundException> qui indique une incompatibilité de filtre d’adresse, vous devez utiliser la classe <xref:System.ServiceModel.Description.ClientViaBehavior> pour diriger les messages vers l’utilitaire de suivi et faire en sorte que l’utilitaire redirige ces messages vers l’adresse du service. La classe <xref:System.ServiceModel.Description.ClientViaBehavior> altère l'en-tête d'adressage `Via` pour spécifier l'adresse réseau suivante séparément du dernier destinataire, indiqué par l'en-tête d'adressage `To` . Ce faisant, en revanche, ne modifiez pas l'adresse du point de terminaison, utilisée pour établir la valeur `To` .  
  
 L'exemple de code suivant présente un exemple de fichier de configuration d'un client.  
  
```xml
<endpoint   
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Qu'est-ce que l'adresse de base ? Comment est-elle liée à une adresse de point de terminaison ?  
 Une adresse de base est l'adresse racine d'une classe <xref:System.ServiceModel.ServiceHost> . Par défaut, si vous ajoutez une classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> dans votre configuration de service, tous les points de terminaison WSDL (Web Services Description Language) que l'hôte publie sont récupérés à partir de l'adresse de base HTTP, plus toute adresse relative fournie au comportement de métadonnées, plus « ?wsdl ». Si vous êtes familiarisé avec ASP.NET et IIS, l’adresse de base est équivalente au répertoire virtuel.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Partage d'un port entre un point de terminaison de service et un point de terminaison mex à l'aide de NetTcpBinding  
 Si vous spécifiez l'adresse de base d'un service en tant que net.tcp://MyServer:8080/MyService et ajoutez les points de terminaison suivants :  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 Et si vous modifiez un des paramètres NetTcpBinding comme illustré dans l'extrait de configuration suivant :  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 Un message d'erreur se présentant comme suit s'affiche : Exception non gérée : System.ServiceModel.AddressAlreadyInUseException : Il existe déjà un écouteur sur le point de terminaison IP 0.0.0.0:9000 Vous pouvez contourner cette erreur en spécifiant une URL complète avec un autre port pour le point de terminaison MEX comme illustré dans l'extrait de configuration suivant :  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Lors de l'appel d'une application HTTP Web WCF à partir d'une application SOAP WCF, le service retourne l'erreur suivante : 405 Méthode non autorisée  
 L’appel d’une application HTTP Web WCF (un service qui utilise les <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>) à partir d’un service WCF peut générer l’exception suivante : ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` cette exception se produit parce que WCF remplace le <xref:System.ServiceModel.OperationContext> sortant par le <xref:System.ServiceModel.OperationContext>entrant. Pour résoudre ce problème, créez un <xref:System.ServiceModel.OperationContextScope> dans l’opération de service HTTP Web WCF. Par exemple :  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Débogage d’erreurs d’authentification Windows](./feature-details/debugging-windows-authentication-errors.md)
