---
title: Fonctionnalités de simplification de WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 28a05053fda8380b55a1a9eee20119b8c4cfccfe
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452654"
---
# <a name="wcf-simplification-features"></a>Fonctionnalités de simplification de WCF

Cette rubrique décrit les nouvelles fonctionnalités qui facilitent l’écriture d’applications WCF.

## <a name="simplified-generated-configuration-files"></a>Fichiers de configuration générés simplifiés

Lorsque vous ajoutez une référence de service dans Visual Studio ou utilisez l'outil SvcUtil.exe, un fichier de configuration client est généré. Dans les versions antérieures de WCF, ces fichiers de configuration contenaient la valeur de chaque propriété de liaison et ce, même si sa valeur était la valeur par défaut. Dans WCF 4.5, les fichiers de configuration générés contiennent uniquement les propriétés de liaison qui ont une valeur non définie par défaut.

L'exemple suivant est un fichier de configuration généré par WCF 3.0.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
                    allowCookies="false" bypassProxyOnLocal="false"
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
                    useDefaultWebProxy="true">
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"
                        maxArrayLength="16384" maxBytesPerRead="4096"
                        maxNameTableCharCount="16384" />
                    <security mode="None">
                        <transport clientCredentialType="None" proxyCredentialType="None"
                            realm="" />
                        <message clientCredentialType="UserName" algorithmSuite="Default" />
                    </security>
                </binding>
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

L'exemple suivant est un fichier de configuration généré par WCF 4.5.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" />
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

## <a name="contract-first-development"></a>Développement Contrat en premier

WCF prend désormais en charge le développement Contrat en premier. L’outil Svcutil. exe possède un commutateur/serviceContract qui vous permet de générer des contrats de service et de données à partir d’un document WSDL.

## <a name="add-service-reference-from-a-portable-subset-project"></a>Ajouter une référence de service d'un projet de sous-ensemble portable

Les projets de sous-ensemble portables permettent aux programmeurs d’assembly .NET de maintenir une arborescence source unique et le système de génération tout en prenant en charge plusieurs implémentations .NET (Desktop, Silverlight, Windows Phone et Xbox). Les projets de sous-ensemble portables référencent uniquement les bibliothèques portables .NET qui sont des assemblys qui peuvent être utilisés sur n’importe quelle implémentation .NET. L'expérience du développeur est identique à celle de l'ajout d'une référence de service dans une autre application cliente WCF. Pour plus d’informations, consultez [Ajouter une référence de service dans un projet de sous-ensemble portable](add-service-reference-in-a-portable-subset-project.md).

## <a name="aspnet-compatibility-mode-default-changed"></a>Modification de la valeur par défaut pour le mode de compatibilité ASP.NET

WCF fournit le mode de compatibilité ASP.NET pour accorder aux développeurs l'accès total aux fonctionnalités dans le pipeline HTTP ASP.NET lors de l'écriture des services WCF. Pour utiliser ce mode, vous devez affecter la valeur true à l’attribut `aspNetCompatibilityEnabled` dans la section [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) de Web. config. En outre, tout service de cet appDomain doit avoir la propriété `RequirementsMode` sur son <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> défini sur <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Par défaut <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> a maintenant la valeur <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> et le modèle d’application de service WCF par défaut définit l’attribut `aspNetCompatibilityEnabled` sur `true`. Pour plus d’informations, consultez [What’s New in Windows Communication Foundation 4,5](whats-new.md) and [WCF services and ASP.net](./feature-details/wcf-services-and-aspnet.md).

## <a name="streaming-improvements"></a>Améliorations de la diffusion en continu

- La prise en charge de la diffusion en continu asynchrone a été ajoutée à WCF. Pour activer la diffusion en continu asynchrone, ajoutez le comportement de point de terminaison <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> à l'hôte de service et affectez à sa propriété <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> la valeur `true`. L'extensibilité peut en tirer parti lorsqu'un service envoie des messages transmis en continu à plusieurs clients qui les lisent lentement. WCF ne bloque plus un thread par client et libère le thread pour prendre en charge un autre client.

- Limitations supprimées concernant la mise en mémoire tampon des messages lorsqu'un service est hébergé par IIS. Dans les versions antérieures de WCF, lors de la réception d'un message pour un service hébergé par IIS qui utilisait le transfert de message en continu, ASP.NET plaçait le message entier en mémoire tampon avant de l'envoyer à WCF. Cela entraînait une grande consommation de mémoire. Cette mise en mémoire tampon a été supprimée dans .NET 4.5 et désormais les services WCF hébergés par IIS peuvent traiter le flux entrant avant que le message entier n'ait été reçu, ce qui permet une réelle diffusion en continu. Cela permet à WCF de répondre immédiatement aux messages et améliore les performances. En outre, vous n'avez plus besoin de spécifier une valeur pour `maxRequestLength`, la limite de taille ASP.NET sur les requêtes entrantes. Si cette propriété est définie, elle est ignorée. Pour plus d’informations sur `maxRequestLength` consultez [\<httpRuntime > élément de configuration](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/e1f13641(v=vs.71)). Vous devrez toujours configurer le maxAllowedContentLength. pour plus d’informations, consultez [limites des demandes IIS](https://docs.microsoft.com/previous-versions/iis/settings-schema/ms689462(v=vs.90)).

## <a name="new-transport-default-values"></a>Valeurs par défaut pour le nouveau transport

Le tableau suivant décrit les paramètres qui ont changé et où trouver des informations supplémentaires.

|Propriété|Il en va|Nouvelle valeur par défaut|Informations complémentaires|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 secondes|Cette propriété détermine la durée pendant laquelle une connexion TCP peut s’authentifier à l’aide du protocole de tramage .NET. Un client doit envoyer des données initiales avant que le serveur dispose de suffisamment d'informations pour exécuter l'authentification. Ce délai d'attente est volontairement plus petit que le ReceiveTimeout (10 minutes) afin que les clients non authentifiés malveillants ne conservent pas longtemps les connexions occupées au serveur. La valeur par défaut correspond à 30 secondes. Pour plus d’informations sur <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * nombre de processeurs|Cette propriété de niveau socket décrit le nombre de demandes en "attente d'acceptation" à mettre en file d'attente. Si la file d’attente du backlog d’écoute est remplie, les nouvelles demandes de socket sont rejetées. Pour plus d’informations sur <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * nombre de processeurs pour le transport<br /><br /> 4 \* nombre de processeurs pour SMSvcHost. exe|Cette propriété limite le nombre de canaux que le serveur peut avoir en attente sur un écouteur. Lorsque MaxPendingAccepts est trop bas, il y a un petit intervalle de temps pendant lequel tous les canaux en attente démarrent les connexions de service, mais aucun nouveau canal ne démarre d'écoute. Une connexion peut se produire pendant cet intervalle et échouera, car aucun élément ne l'attend sur le serveur. Cette propriété peut être configurée en affectant un plus grand nombre à la propriété <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>. Pour plus d’informations, consultez <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> et [configuration du service de partage de ports net. TCP.](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * nombre de processeurs|Cette propriété détermine le nombre de connexions acceptées par un transport, mais non choisies par le répartiteur ServiceModel. Pour définir cette valeur, utilisez `MaxConnections` sur la liaison ou `maxOutboundConnectionsPerEndpoint` sur l'élément de liaison. Pour plus d’informations sur <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 secondes|Cette propriété spécifie le délai d'attente pour lire les données d'encadrement TCP et effectuer la distribution de la connexion à partir des connexions sous-jacentes. Elle permet de limiter la durée pendant laquelle le service SMSvcHost.exe prend part à la lecture des données de préambule d'une connexion entrante. Pour plus d’informations, consultez [configuration du service de partage de ports net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md).|

> [!NOTE]
> Ces nouvelles valeurs par défaut sont utilisées uniquement si vous déployez le service WCF sur un ordinateur avec le .NET Framework 4.5. Si vous déployez le même service sur un ordinateur avec le .NET Framework 4.0, les valeurs par défaut du .NET Framework 4.0 sont utilisées. Dans ce cas, il est recommandé de configurer ces paramètres explicitement.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> contient des valeurs de quota configurables pour les lecteurs du dictionnaire XML qui limitent la quantité de mémoire utilisée par un encodeur lors de la création d'un message. Bien que ces quotas soient configurables, les valeurs par défaut ont changé pour réduire le risque qu'un développeur doivent les définir explicitement. Le quota `MaxReceivedMessageSize` n'a pas été modifié afin qu'il puisse toujours limiter la consommation de mémoire, ce qui vous évite d'avoir à gérer la complexité de <xref:System.Xml.XmlDictionaryReaderQuotas>. Le tableau suivant contient les quotas, leurs nouvelles valeurs par défaut et une brève explication de leur utilisation.

|Nom du quota|Valeur par défaut|Description|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|Obtient et définit la longueur maximale de tableau autorisée. Ce quota limite la taille maximale d'un tableau de primitives que le lecteur XML renvoie, notamment un tableau d'octets. Ce quota ne limite pas la consommation de mémoire dans le lecteur XML lui-même, mais dans le composant qui utilise le lecteur. Par exemple, lorsque <xref:System.Runtime.Serialization.DataContractSerializer> utilise un lecteur sécurisé avec <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, il ne désérialise pas les tableaux d'octets supérieurs à ce quota.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Obtient et définit le nombre maximal d'octets autorisés retournés pour chaque lecture. Ce quota limite le nombre d’octets lus dans une seule opération de lecture lors de la lecture de l’étiquette de début d’élément et ses attributs. (Dans les cas non diffusés en continu, le nom de l'élément lui-même n'est pas compté dans le quota.) Un nombre trop élevé d'attributs XML risque d'utiliser un temps de traitement disproportionné parce que le caractère unique des noms d'attributs doit être vérifié. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> atténue cette menace.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 nœuds|Ce quota limite la profondeur d'imbrication maximale des éléments XML. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> interagit avec <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: le lecteur conserve toujours des données en mémoire pour l'élément actuel et tous ses ancêtres, donc la consommation de mémoire maximale du lecteur est proportionnelle au produit de ces deux paramètres. Lors de la désérialisation d'un graphique d'objets très imbriqué, le désérialiseur est obligé d'accéder à la pile entière et de lever une exception <xref:System.StackOverflowException>irrécupérable. Une corrélation directe existe entre l'imbrication XML et l'imbrication d'objets pour <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> permet d'atténuer cette menace.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Ce quota limite le nombre maximal de caractères autorisés dans un nametable. Le nametable contient certaines chaînes (telles que des espaces de noms et des préfixes) rencontrées lors du traitement d'un document XML. Étant donné que ces chaînes sont mises en mémoire tampon, ce quota permet d'empêcher une mise en mémoire tampon excessive lorsqu'une diffusion en continu est prévue.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Ce quota limite la taille maximale de la chaîne que le lecteur XML renvoie. Ce quota ne limite pas la consommation de mémoire dans le lecteur XML lui-même, mais dans le composant qui utilise le lecteur. Par exemple, lorsque <xref:System.Runtime.Serialization.DataContractSerializer> utilise un lecteur sécurisé avec <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, il ne désérialise pas les chaînes supérieures à ce quota.|

> [!IMPORTANT]
> Pour plus d’informations sur la sécurisation de vos données, consultez « Utilisation de XML en toute sécurité » sous [considérations de sécurité pour les données](./feature-details/security-considerations-for-data.md) .

> [!NOTE]
> Ces nouvelles valeurs par défaut sont utilisées uniquement si vous déployez le service WCF sur un ordinateur avec le .NET Framework 4.5. Si vous déployez le même service sur un ordinateur avec le .NET Framework 4.0, les valeurs par défaut du .NET Framework 4.0 sont utilisées. Dans ce cas, il est recommandé de configurer ces paramètres explicitement.

## <a name="wcf-configuration-validation"></a>Validation de configuration WCF

Dans le cadre du processus de génération dans Visual Studio, les fichiers de configuration WCF sont maintenant validés. Une liste d’erreurs ou d’avertissements de validation s’affiche dans Visual Studio si la validation échoue.

## <a name="xml-editor-tooltips"></a>Info-bulles de l'éditeur XML

Pour aider les développeurs de services WCF nouveaux et existants à configurer leurs services, l'Éditeur XML de Visual Studio fournit maintenant des info-bulles pour chaque élément de configuration et ses propriétés qui fait partie du fichier de configuration du service.

## <a name="basichttpbinding-improvements"></a>Améliorations de BasicHttpBinding

1. Permet à un seul point de terminaison WCF de répondre à différents modes d'authentification.

2. Permet aux paramètres de sécurité d'un service WCF d'être contrôlés par IIS
