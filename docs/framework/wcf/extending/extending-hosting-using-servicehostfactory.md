---
title: Extension de l'hébergement à l'aide de ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: d2224ea683326679efdad368cf2ff7b2b95f4dba
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273124"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Extension de l'hébergement à l'aide de ServiceHostFactory

L' <xref:System.ServiceModel.ServiceHost> API standard pour les services d’hébergement dans Windows Communication Foundation (WCF) est un point d’extensibilité dans l’architecture WCF. Les utilisateurs peuvent dériver leurs propres classes d'hôte de <xref:System.ServiceModel.ServiceHost>, habituellement pour substituer <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> et utiliser <xref:System.ServiceModel.Description.ServiceDescription> afin d'ajouter des points de terminaison par défaut de façon impérative ou modifier des comportements, avant d'ouvrir le service.  
  
 Dans l'environnement auto-hébergé, vous ne devez pas créer un <xref:System.ServiceModel.ServiceHost> personnalisé parce que vous écrivez le code qui instancie l'hôte puis appelle <xref:System.ServiceModel.ICommunicationObject.Open> après l'avoir instancié. Entre ces deux étapes, vous pouvez faire ce que vous souhaitiez. Par exemple, vous pouvez ajouter un nouveau <xref:System.ServiceModel.Description.IServiceBehavior> :  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Cette approche n'est pas réutilisable. Le code qui manipule la description est codé dans le programme hôte (dans ce cas, la fonction Main()), il est donc difficile de réutiliser cette logique dans d'autres contextes. Il y a également d'autres façons d'ajouter un <xref:System.ServiceModel.Description.IServiceBehavior> qui ne requiert pas de code impératif. Vous pouvez dériver un attribut de <xref:System.ServiceModel.ServiceBehaviorAttribute> et mettre cela sur le type d'implémentation de votre service ou vous pouvez créer un comportement personnalisé configurable et le composer dynamiquement à l'aide de la configuration.  
  
 Toutefois, le problème peut également être résolu en modifiant légèrement l'exemple. Une approche possible consiste à déplacer le code qui ajoute ServiceBehavior hors de `Main()` et le placer dans la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> d'une dérivée personnalisée de <xref:System.ServiceModel.ServiceHost>:  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 Dans `Main()`, vous pouvez ensuite utiliser :  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Vous avez ainsi encapsulé la logique personnalisée dans une abstraction vierge qui peut être facilement réutilisée dans de nombreux exécutables d'hôte différents.  
  
 Il n'est pas évident de savoir comment utiliser cette version <xref:System.ServiceModel.ServiceHost> personnalisée dans IIS (Internet Information Services) ou dans le service d'activation de processus de Windows (WAS). Ces environnements sont différents de l'environnement auto-hébergé, car l'environnement d'hébergement est celui qui instancie le <xref:System.ServiceModel.ServiceHost> pour le compte de l'application. L'infrastructure d'hébergement IIS et WAS ne connaît rien de votre dérivée <xref:System.ServiceModel.ServiceHost> personnalisée.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> a été conçu pour résoudre ce problème d'accès à votre <xref:System.ServiceModel.ServiceHost> personnalisé dans IIS ou WAS. Parce qu'un hôte personnalisé dérivé de <xref:System.ServiceModel.ServiceHost> est configuré dynamiquement et appartient potentiellement à des types différents, l'environnement d'hébergement ne l'instancie jamais directement. Au lieu de cela, WCF utilise un modèle de fabrique pour fournir une couche d’indirection entre l’environnement d’hébergement et le type concret du service. À moins que vous lui indiquiez d'agir autrement, il utilise une implémentation par défaut de <xref:System.ServiceModel.Activation.ServiceHostFactory> qui retourne une instance de <xref:System.ServiceModel.ServiceHost>. Toutefois, vous pouvez également fournir votre propre fabrique qui retourne votre hôte dérivé en spécifiant le nom de type CLR de votre implémentation de fabrique dans la @ServiceHost directive.  
  
 Le but est que pour les cas de base, l'implémentation de votre propre fabrique soit un exercice simple. Par exemple, voici un <xref:System.ServiceModel.Activation.ServiceHostFactory> personnalisé qui retourne un <xref:System.ServiceModel.ServiceHost>dérivé :  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Pour utiliser cette fabrique au lieu de la fabrique par défaut, fournissez le nom de type dans la @ServiceHost directive comme suit :  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 Bien qu'il n'y ait aucune limitation technique en ce qui concerne ce que vous pouvez faire au niveau du <xref:System.ServiceModel.ServiceHost> que vous avez retourné de <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, nous vous suggérons de garder vos implémentations de fabrique aussi simples que possible. Si vous avez beaucoup de logique personnalisée, il est préférable de placer cette logique à l’intérieur de votre hôte au lieu de l’intérieur de la fabrique afin qu’il puisse être réutilisable.  
  
 Il existe une autre couche de l'API d'hébergement qui doit être indiquée ici. WCF possède également <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> , à partir duquel <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.Activation.ServiceHostFactory> dérivent respectivement. Ceux-ci sont prévus pour des scénarios plus avancés où vous devez permuter des parties importantes du système de métadonnées avec vos propres créations personnalisées.
