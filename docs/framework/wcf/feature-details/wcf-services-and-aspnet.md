---
title: Services WCF et ASP.NET
description: Découvrez comment héberger des services WCF côte à côte avec ASP.NET et les héberger en mode de compatibilité ASP.NET.
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 765a509f94a0a934cdbbf0212cfc1d4053d29f9c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553315"
---
# <a name="wcf-services-and-aspnet"></a>Services WCF et ASP.NET

Cette rubrique explique comment héberger des services Windows Communication Foundation (WCF) côte à côte avec ASP.NET et les héberger en mode de compatibilité ASP.NET.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hébergement de WCF côte à côte avec ASP.NET

Les services WCF hébergés dans Internet Information Services (IIS) peuvent se trouver avec. Les pages ASPX et les services Web ASMX à l’intérieur d’un domaine d’application unique et commun. ASP.NET fournit des services d’infrastructure communs tels que la gestion AppDomain et la compilation dynamique pour WCF et le runtime HTTP ASP.NET. La configuration par défaut pour WCF est côte à côte avec ASP.NET.

![Capture d’écran montrant les services WCF et ASP .NET : partage de l’État.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

Le runtime HTTP ASP.NET gère les demandes ASP.NET, mais ne participe pas au traitement des demandes destinées aux services WCF, bien que ces services soient hébergés dans le même AppDomain que le contenu ASP.NET. Au lieu de cela, le modèle de service WCF intercepte les messages adressés aux services WCF et les achemine via la pile de transport/canal WCF.

Les résultats du modèle côte à côte est le suivant :

- ASP.NET et les services WCF peuvent partager l’État AppDomain. Étant donné que les deux infrastructures peuvent coexister dans le même AppDomain, WCF peut également partager l’État AppDomain avec ASP.NET (y compris les variables statiques, les événements, etc.).

- Les services WCF se comportent de façon cohérente, indépendamment de l’environnement d’hébergement et du transport. L'exécution d'ASP.NET HTTP est intentionnellement associée à l'environnement d'hébergement de IIS/ASP.NET et à la communication HTTP. À l’inverse, WCF est conçu pour se comporter de manière cohérente dans les environnements d’hébergement (WCF se comporte de manière cohérente à l’intérieur et à l’extérieur d’IIS) et entre les transports (un service hébergé dans IIS 7,0 et ultérieur a un comportement cohérent sur tous les points de terminaison qu’il expose, même si certains de ces points de terminaison utilisent des protocoles autres que HTTP

- Dans un AppDomain, les fonctionnalités implémentées par le runtime HTTP s’appliquent au contenu ASP.NET, mais pas à WCF. De nombreuses fonctionnalités spécifiques à HTTP de la plate-forme d’application ASP.NET ne s’appliquent pas aux services WCF hébergés dans un AppDomain qui contient du contenu ASP.NET. Voici des exemples de ces fonctionnalités :

  - HttpContext : <xref:System.Web.HttpContext.Current%2A> est toujours `null` lorsqu’il est accessible à partir d’un service WCF. Utilisez plutôt <xref:System.ServiceModel.Channels.RequestContext>.

  - Autorisation basée sur les fichiers : le modèle de sécurité WCF n’autorise pas la liste de contrôle d’accès (ACL) appliquée au fichier. svc du service lorsque vous décidez si une demande de service est autorisée.

  - Autorisation d’URL basée sur la configuration : de la même façon, le modèle de sécurité WCF n’adhère à aucune règle d’autorisation basée sur l’URL spécifiée dans l’élément de configuration de System. Web \<authorization> . Ces paramètres sont ignorés pour les demandes WCF si un service réside dans un espace d’URL sécurisé par ASP. Règles d’autorisation d’URL du réseau.

  - Extensibilité de l’HttpModule : l’infrastructure d’hébergement WCF intercepte les demandes WCF lorsque l' <xref:System.Web.HttpApplication.PostAuthenticateRequest> événement est déclenché et ne renvoie pas le traitement au pipeline HTTP ASP.net. Les modules codés pour intercepter les demandes à des étapes ultérieures du pipeline n’interceptent pas les demandes WCF.

  - Emprunt d’identité ASP.NET : par défaut, les demandes WCF s’exécutent toujours comme l’identité de processus IIS, même si ASP.NET est défini pour activer l’emprunt d’identité à l’aide de l’option de configuration de System. Web \<identity impersonate="true" /> .

Ces restrictions s’appliquent uniquement aux services WCF hébergés dans une application IIS. Le comportement du contenu ASP.NET n’est pas affecté par la présence de WCF.

Les applications WCF qui requièrent des fonctionnalités traditionnellement fournies par le pipeline HTTP doivent envisager d’utiliser les équivalents WCF, qui sont indépendants des hôtes et du transport :

- <xref:System.ServiceModel.OperationContext> plutôt que <xref:System.Web.HttpContext>.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> au lieu de l'autorisation de fichier/URL de ASP.NET.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ou des canaux en couche personnalisés au lieu des modules HTTP.

- Emprunt d’identité pour chaque opération à l’aide de WCF au lieu de l’emprunt d’identité System. Web.

Vous pouvez également envisager d’exécuter vos services dans le mode de compatibilité ASP.NET de WCF.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hébergement des services WCF en mode de compatibilité ASP.NET

Bien que le modèle WCF soit conçu pour se comporter de manière cohérente dans les environnements d’hébergement et les transports, il existe souvent des scénarios dans lesquels une application n’a pas besoin de ce niveau de flexibilité. Le mode de compatibilité ASP.NET de WCF est approprié pour les scénarios qui ne nécessitent pas l’hébergement en dehors d’IIS ou pour communiquer via des protocoles autres que HTTP, mais qui utilisent toutes les fonctionnalités de la plateforme d’application Web ASP.NET.

Contrairement à la configuration côte à côte par défaut, où l’infrastructure d’hébergement WCF intercepte les messages WCF et les achemine à partir du pipeline HTTP, les services WCF qui s’exécutent en mode de compatibilité ASP.NET participent pleinement au cycle de vie des demandes HTTP ASP.NET. En mode de compatibilité, les services WCF utilisent le pipeline HTTP via une <xref:System.Web.IHttpHandler> implémentation, de la même façon que les requêtes pour les pages aspx et les services Web ASMX sont gérés. Par conséquent, WCF se comporte de la même façon que ASMX en ce qui concerne les fonctionnalités ASP.NET suivantes :

- <xref:System.Web.HttpContext>: Les services WCF qui s’exécutent en mode de compatibilité ASP.NET peuvent accéder à <xref:System.Web.HttpContext.Current%2A> et à son état associé.

- Autorisation basée sur les fichiers : les services WCF qui s’exécutent en mode de compatibilité ASP.NET peuvent être sécurisés en attachant des listes de contrôle d’accès (ACL) du système de fichiers au fichier. svc du service.

- Autorisation configurable d’URL : ASP. Les règles d’autorisation d’URL du réseau sont appliquées pour les demandes WCF lorsque le service WCF s’exécute en mode de compatibilité ASP.NET.

- <xref:System.Web.HttpModuleCollection> Extensibilité : étant donné que les services WCF qui s’exécutent en mode de compatibilité ASP.NET participent pleinement au cycle de vie des demandes HTTP ASP.NET, tout module HTTP configuré dans le pipeline HTTP peut fonctionner sur les demandes WCF avant et après l’appel du service.

- Emprunt d’identité ASP.NET : les services WCF s’exécutent à l’aide de l’identité actuelle du thread ASP.NET représenté, qui peut être différent de l’identité du processus IIS si l’emprunt d’identité ASP.NET a été activé pour l’application. Si l’emprunt d’identité ASP.NET et l’emprunt d’identité WCF sont tous deux activés pour une opération de service particulière, l’implémentation de service s’exécute finalement à l’aide de l’identité obtenue à partir de WCF.

Le mode de compatibilité ASP.NET de WCF est activé au niveau de l’application via la configuration suivante (située dans le fichier Web.config de l’application) :

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

La valeur par défaut est `false` si elle n’est pas spécifiée. La valeur `false` indique que tous les services WCF qui s’exécutent dans l’application ne s’exécutent pas en mode de compatibilité ASP.net.

Étant donné que le mode de compatibilité ASP.NET implique une sémantique de traitement des demandes fondamentalement différente de la valeur par défaut de WCF, les implémentations de service individuelles peuvent contrôler si elles s’exécutent à l’intérieur d’une application pour laquelle le mode de compatibilité ASP.NET a été activé. Les services peuvent utiliser <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> pour indiquer s'ils prennent en charge le mode de compatibilité ASP.NET. La valeur par défaut de cet attribut est <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

Le tableau suivant illustre comment le paramètre de mode de compatibilité défini au niveau de l'application interagit avec le niveau de prise en charge déclaré du service :

|Paramètre de mode de compatibilité défini au niveau de l'application|[AspNetCompatibilityRequirementsMode]<br /><br /> Paramètre|Résultat observé|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Le service est activé.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Le service est activé.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Une erreur d'activation se produit lorsque le service reçoit un message.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Une erreur d'activation se produit lorsque le service reçoit un message.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Le service est activé.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Le service est activé.|

> [!NOTE]
> IIS 7,0 et WAS permet aux services WCF de communiquer via des protocoles autres que HTTP. Toutefois, les services WCF qui s’exécutent dans les applications qui ont activé le mode de compatibilité ASP.NET ne sont pas autorisés à exposer des points de terminaison non-HTTP. Une telle configuration génère une exception d'activation lorsque le service reçoit son premier message.

Pour plus d’informations sur l’activation du mode de compatibilité ASP.NET pour les services WCF, consultez <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> et l’exemple de [compatibilité ASP.net](../samples/aspnet-compatibility.md) .

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))
