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
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="0d7e0-102">Extension de l'hébergement à l'aide de ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="0d7e0-102">Extending Hosting Using ServiceHostFactory</span></span>

<span data-ttu-id="0d7e0-103">L' <xref:System.ServiceModel.ServiceHost> API standard pour les services d’hébergement dans Windows Communication Foundation (WCF) est un point d’extensibilité dans l’architecture WCF.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="0d7e0-104">Les utilisateurs peuvent dériver leurs propres classes d'hôte de <xref:System.ServiceModel.ServiceHost>, habituellement pour substituer <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> et utiliser <xref:System.ServiceModel.Description.ServiceDescription> afin d'ajouter des points de terminaison par défaut de façon impérative ou modifier des comportements, avant d'ouvrir le service.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="0d7e0-105">Dans l'environnement auto-hébergé, vous ne devez pas créer un <xref:System.ServiceModel.ServiceHost> personnalisé parce que vous écrivez le code qui instancie l'hôte puis appelle <xref:System.ServiceModel.ICommunicationObject.Open> après l'avoir instancié.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="0d7e0-106">Entre ces deux étapes, vous pouvez faire ce que vous souhaitiez.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="0d7e0-107">Par exemple, vous pouvez ajouter un nouveau <xref:System.ServiceModel.Description.IServiceBehavior> :</span><span class="sxs-lookup"><span data-stu-id="0d7e0-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0d7e0-108">Cette approche n'est pas réutilisable.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-108">This approach is not reusable.</span></span> <span data-ttu-id="0d7e0-109">Le code qui manipule la description est codé dans le programme hôte (dans ce cas, la fonction Main()), il est donc difficile de réutiliser cette logique dans d'autres contextes.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="0d7e0-110">Il y a également d'autres façons d'ajouter un <xref:System.ServiceModel.Description.IServiceBehavior> qui ne requiert pas de code impératif.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="0d7e0-111">Vous pouvez dériver un attribut de <xref:System.ServiceModel.ServiceBehaviorAttribute> et mettre cela sur le type d'implémentation de votre service ou vous pouvez créer un comportement personnalisé configurable et le composer dynamiquement à l'aide de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="0d7e0-112">Toutefois, le problème peut également être résolu en modifiant légèrement l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="0d7e0-113">Une approche possible consiste à déplacer le code qui ajoute ServiceBehavior hors de `Main()` et le placer dans la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> d'une dérivée personnalisée de <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="0d7e0-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
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
  
 <span data-ttu-id="0d7e0-114">Dans `Main()`, vous pouvez ensuite utiliser :</span><span class="sxs-lookup"><span data-stu-id="0d7e0-114">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0d7e0-115">Vous avez ainsi encapsulé la logique personnalisée dans une abstraction vierge qui peut être facilement réutilisée dans de nombreux exécutables d'hôte différents.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="0d7e0-116">Il n'est pas évident de savoir comment utiliser cette version <xref:System.ServiceModel.ServiceHost> personnalisée dans IIS (Internet Information Services) ou dans le service d'activation de processus de Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="0d7e0-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="0d7e0-117">Ces environnements sont différents de l'environnement auto-hébergé, car l'environnement d'hébergement est celui qui instancie le <xref:System.ServiceModel.ServiceHost> pour le compte de l'application.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="0d7e0-118">L'infrastructure d'hébergement IIS et WAS ne connaît rien de votre dérivée <xref:System.ServiceModel.ServiceHost> personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="0d7e0-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> a été conçu pour résoudre ce problème d'accès à votre <xref:System.ServiceModel.ServiceHost> personnalisé dans IIS ou WAS.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="0d7e0-120">Parce qu'un hôte personnalisé dérivé de <xref:System.ServiceModel.ServiceHost> est configuré dynamiquement et appartient potentiellement à des types différents, l'environnement d'hébergement ne l'instancie jamais directement.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="0d7e0-121">Au lieu de cela, WCF utilise un modèle de fabrique pour fournir une couche d’indirection entre l’environnement d’hébergement et le type concret du service.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="0d7e0-122">À moins que vous lui indiquiez d'agir autrement, il utilise une implémentation par défaut de <xref:System.ServiceModel.Activation.ServiceHostFactory> qui retourne une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="0d7e0-123">Toutefois, vous pouvez également fournir votre propre fabrique qui retourne votre hôte dérivé en spécifiant le nom de type CLR de votre implémentation de fabrique dans la @ServiceHost directive.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="0d7e0-124">Le but est que pour les cas de base, l'implémentation de votre propre fabrique soit un exercice simple.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="0d7e0-125">Par exemple, voici un <xref:System.ServiceModel.Activation.ServiceHostFactory> personnalisé qui retourne un <xref:System.ServiceModel.ServiceHost>dérivé :</span><span class="sxs-lookup"><span data-stu-id="0d7e0-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="0d7e0-126">Pour utiliser cette fabrique au lieu de la fabrique par défaut, fournissez le nom de type dans la @ServiceHost directive comme suit :</span><span class="sxs-lookup"><span data-stu-id="0d7e0-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="0d7e0-127">Bien qu'il n'y ait aucune limitation technique en ce qui concerne ce que vous pouvez faire au niveau du <xref:System.ServiceModel.ServiceHost> que vous avez retourné de <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, nous vous suggérons de garder vos implémentations de fabrique aussi simples que possible.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="0d7e0-128">Si vous avez beaucoup de logique personnalisée, il est préférable de placer cette logique à l’intérieur de votre hôte au lieu de l’intérieur de la fabrique afin qu’il puisse être réutilisable.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-128">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="0d7e0-129">Il existe une autre couche de l'API d'hébergement qui doit être indiquée ici.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="0d7e0-130">WCF possède également <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> , à partir duquel <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.Activation.ServiceHostFactory> dérivent respectivement.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="0d7e0-131">Ceux-ci sont prévus pour des scénarios plus avancés où vous devez permuter des parties importantes du système de métadonnées avec vos propres créations personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
