---
title: Instructions relatives à l’injection de dépendances
description: Découvrez les différentes recommandations en matière d’injection de dépendances et les meilleures pratiques pour le développement d’applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: guide
ms.openlocfilehash: a8d52642b9217c7340db69494624d8ab85ea6c92
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247896"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="b876a-103">Instructions relatives à l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="b876a-103">Dependency injection guidelines</span></span>

<span data-ttu-id="b876a-104">Cet article fournit des recommandations générales et les meilleures pratiques pour implémenter l’injection de dépendances dans les applications .NET.</span><span class="sxs-lookup"><span data-stu-id="b876a-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="b876a-105">Conception de services pour l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="b876a-105">Design services for dependency injection</span></span>

<span data-ttu-id="b876a-106">Lors de la conception de services pour l’injection de dépendances :</span><span class="sxs-lookup"><span data-stu-id="b876a-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="b876a-107">Évitez les classes et les membres avec état, static.</span><span class="sxs-lookup"><span data-stu-id="b876a-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="b876a-108">Évitez de créer un état global en concevant des applications qui utilisent des services Singleton à la place.</span><span class="sxs-lookup"><span data-stu-id="b876a-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="b876a-109">Éviter une instanciation directe de classes dépendantes au sein de services.</span><span class="sxs-lookup"><span data-stu-id="b876a-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="b876a-110">L’instanciation directe associe le code à une implémentation particulière.</span><span class="sxs-lookup"><span data-stu-id="b876a-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="b876a-111">Rendez les services petits, bien factorisés et faciles à tester.</span><span class="sxs-lookup"><span data-stu-id="b876a-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="b876a-112">Si une classe possède de nombreuses dépendances injectées, il peut s’agir d’un signe que la classe a trop de responsabilités et viole le [principe de responsabilité unique (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span><span class="sxs-lookup"><span data-stu-id="b876a-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="b876a-113">Essayez de refactoriser la classe en déplaçant certaines de ses responsabilités dans de nouvelles classes.</span><span class="sxs-lookup"><span data-stu-id="b876a-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="b876a-114">Suppression des services</span><span class="sxs-lookup"><span data-stu-id="b876a-114">Disposal of services</span></span>

<span data-ttu-id="b876a-115">Le conteneur est responsable du nettoyage des types qu’il crée et appelle <xref:System.IDisposable.Dispose%2A> sur les <xref:System.IDisposable> instances.</span><span class="sxs-lookup"><span data-stu-id="b876a-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="b876a-116">Les services résolus à partir du conteneur ne doivent jamais être supprimés par le développeur.</span><span class="sxs-lookup"><span data-stu-id="b876a-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="b876a-117">Si un type ou une fabrique est inscrit en tant que singleton, le conteneur supprime automatiquement le singleton.</span><span class="sxs-lookup"><span data-stu-id="b876a-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="b876a-118">Dans l’exemple suivant, les services sont créés par le conteneur de service et supprimés automatiquement :</span><span class="sxs-lookup"><span data-stu-id="b876a-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

<span data-ttu-id="b876a-119">La console de débogage affiche l’exemple de sortie suivant après l’exécution de :</span><span class="sxs-lookup"><span data-stu-id="b876a-119">The debug console shows the following sample output after running:</span></span>

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="b876a-120">Services non créés par le conteneur de service</span><span class="sxs-lookup"><span data-stu-id="b876a-120">Services not created by the service container</span></span>

<span data-ttu-id="b876a-121">Considérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b876a-121">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="b876a-122">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="b876a-122">In the preceding code:</span></span>

- <span data-ttu-id="b876a-123">L' `ExampleService` instance n’est **pas** créée par le conteneur de service.</span><span class="sxs-lookup"><span data-stu-id="b876a-123">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="b876a-124">L’infrastructure ne supprime **pas** automatiquement les services.</span><span class="sxs-lookup"><span data-stu-id="b876a-124">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="b876a-125">Le développeur est responsable de la suppression des services.</span><span class="sxs-lookup"><span data-stu-id="b876a-125">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="b876a-126">Recommandations IDisposable pour les instances temporaires et partagées</span><span class="sxs-lookup"><span data-stu-id="b876a-126">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="b876a-127">Transitoire, durée de vie limitée</span><span class="sxs-lookup"><span data-stu-id="b876a-127">Transient, limited lifetime</span></span>

<span data-ttu-id="b876a-128">**Scénario**</span><span class="sxs-lookup"><span data-stu-id="b876a-128">**Scenario**</span></span>

<span data-ttu-id="b876a-129">L’application requiert une <xref:System.IDisposable> instance avec une durée de vie transitoire pour l’un des scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="b876a-129">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="b876a-130">L’instance est résolue dans l’étendue racine (conteneur racine).</span><span class="sxs-lookup"><span data-stu-id="b876a-130">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="b876a-131">L’instance doit être supprimée avant la fin de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="b876a-131">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="b876a-132">**Solution**</span><span class="sxs-lookup"><span data-stu-id="b876a-132">**Solution**</span></span>

<span data-ttu-id="b876a-133">Utilisez le modèle de fabrique pour créer une instance en dehors de l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="b876a-133">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="b876a-134">Dans ce cas, l’application a généralement une `Create` méthode qui appelle directement le constructeur du type final.</span><span class="sxs-lookup"><span data-stu-id="b876a-134">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="b876a-135">Si le type final a d’autres dépendances, la fabrique peut :</span><span class="sxs-lookup"><span data-stu-id="b876a-135">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="b876a-136">Recevoir un <xref:System.IServiceProvider> dans son constructeur.</span><span class="sxs-lookup"><span data-stu-id="b876a-136">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="b876a-137">Utilisez <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> pour instancier l’instance en dehors du conteneur, tout en utilisant le conteneur pour ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="b876a-137">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="b876a-138">Instance partagée, durée de vie limitée</span><span class="sxs-lookup"><span data-stu-id="b876a-138">Shared instance, limited lifetime</span></span>

<span data-ttu-id="b876a-139">**Scénario**</span><span class="sxs-lookup"><span data-stu-id="b876a-139">**Scenario**</span></span>

<span data-ttu-id="b876a-140">L’application requiert une <xref:System.IDisposable> instance partagée sur plusieurs services, mais l' <xref:System.IDisposable> instance doit avoir une durée de vie limitée.</span><span class="sxs-lookup"><span data-stu-id="b876a-140">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="b876a-141">**Solution**</span><span class="sxs-lookup"><span data-stu-id="b876a-141">**Solution**</span></span>

<span data-ttu-id="b876a-142">Inscrivez l’instance avec une durée de vie limitée.</span><span class="sxs-lookup"><span data-stu-id="b876a-142">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="b876a-143">Utilisez <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> pour créer un <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="b876a-143">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="b876a-144">Utilisez les étendues <xref:System.IServiceProvider> pour accéder aux services requis.</span><span class="sxs-lookup"><span data-stu-id="b876a-144">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="b876a-145">Supprimez l’étendue lorsqu’elle n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b876a-145">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="b876a-146">`IDisposable`Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="b876a-146">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="b876a-147">N’inscrivez pas <xref:System.IDisposable> les instances avec une durée de vie transitoire.</span><span class="sxs-lookup"><span data-stu-id="b876a-147">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="b876a-148">Utilisez à la place le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="b876a-148">Use the factory pattern instead.</span></span>
- <span data-ttu-id="b876a-149">Ne résolvez pas <xref:System.IDisposable> les instances avec une durée de vie transitoire ou limitée dans l’étendue racine.</span><span class="sxs-lookup"><span data-stu-id="b876a-149">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="b876a-150">La seule exception à cela est que l’application crée/recrée et supprime <xref:System.IServiceProvider> , mais ce n’est pas un modèle idéal.</span><span class="sxs-lookup"><span data-stu-id="b876a-150">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="b876a-151">La réception d’une <xref:System.IDisposable> dépendance via l’injection de dépendances ne nécessite pas que le récepteur s’implémente <xref:System.IDisposable> lui-même.</span><span class="sxs-lookup"><span data-stu-id="b876a-151">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="b876a-152">Le récepteur de la <xref:System.IDisposable> dépendance ne doit pas appeler <xref:System.IDisposable.Dispose%2A> sur cette dépendance.</span><span class="sxs-lookup"><span data-stu-id="b876a-152">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="b876a-153">Utilisez des étendues pour contrôler les durées de vie des services.</span><span class="sxs-lookup"><span data-stu-id="b876a-153">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="b876a-154">Les étendues ne sont pas hiérarchiques, et il n’existe pas de connexion spéciale entre les étendues.</span><span class="sxs-lookup"><span data-stu-id="b876a-154">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="b876a-155">Pour plus d’informations sur le nettoyage des ressources, consultez [implémenter une méthode dispose](../../standard/garbage-collection/implementing-dispose.md)</span><span class="sxs-lookup"><span data-stu-id="b876a-155">For more information on resource cleanup, see [Implement a Dispose method](../../standard/garbage-collection/implementing-dispose.md)</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="b876a-156">Remplacement de conteneur de services par défaut</span><span class="sxs-lookup"><span data-stu-id="b876a-156">Default service container replacement</span></span>

<span data-ttu-id="b876a-157">Le conteneur de service intégré est conçu pour répondre aux besoins de l’infrastructure et de la plupart des applications grand public.</span><span class="sxs-lookup"><span data-stu-id="b876a-157">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="b876a-158">Nous vous recommandons d’utiliser le conteneur intégré, sauf si vous avez besoin d’une fonctionnalité spécifique qu’il ne prend pas en charge, par exemple :</span><span class="sxs-lookup"><span data-stu-id="b876a-158">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="b876a-159">Injection de propriétés</span><span class="sxs-lookup"><span data-stu-id="b876a-159">Property injection</span></span>
- <span data-ttu-id="b876a-160">Injection en fonction du nom</span><span class="sxs-lookup"><span data-stu-id="b876a-160">Injection based on name</span></span>
- <span data-ttu-id="b876a-161">Conteneurs enfants</span><span class="sxs-lookup"><span data-stu-id="b876a-161">Child containers</span></span>
- <span data-ttu-id="b876a-162">Gestion personnalisée de la durée de vie</span><span class="sxs-lookup"><span data-stu-id="b876a-162">Custom lifetime management</span></span>
- <span data-ttu-id="b876a-163">`Func<T>` prend en charge l’initialisation tardive</span><span class="sxs-lookup"><span data-stu-id="b876a-163">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="b876a-164">Inscription basée sur une convention</span><span class="sxs-lookup"><span data-stu-id="b876a-164">Convention-based registration</span></span>

<span data-ttu-id="b876a-165">Les conteneurs tiers suivants peuvent être utilisés avec les applications ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="b876a-165">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="b876a-166">Autofac</span><span class="sxs-lookup"><span data-stu-id="b876a-166">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="b876a-167">DryIoc</span><span class="sxs-lookup"><span data-stu-id="b876a-167">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="b876a-168">Grace</span><span class="sxs-lookup"><span data-stu-id="b876a-168">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="b876a-169">LightInject</span><span class="sxs-lookup"><span data-stu-id="b876a-169">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="b876a-170">Lamar</span><span class="sxs-lookup"><span data-stu-id="b876a-170">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="b876a-171">Stashbox</span><span class="sxs-lookup"><span data-stu-id="b876a-171">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="b876a-172">Unity</span><span class="sxs-lookup"><span data-stu-id="b876a-172">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="b876a-173">Sécurité des threads</span><span class="sxs-lookup"><span data-stu-id="b876a-173">Thread safety</span></span>

<span data-ttu-id="b876a-174">Créez des services singleton thread-safe.</span><span class="sxs-lookup"><span data-stu-id="b876a-174">Create thread-safe singleton services.</span></span> <span data-ttu-id="b876a-175">Si un service Singleton a une dépendance vis-à-vis d’un service temporaire, le service temporaire peut également nécessiter la sécurité des threads en fonction de la façon dont il est utilisé par le singleton.</span><span class="sxs-lookup"><span data-stu-id="b876a-175">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="b876a-176">La méthode de fabrique d’un service unique, telle que le deuxième argument de [AddSingleton \<TService> (IServiceCollection, Func \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), n’a pas besoin d’être thread-safe.</span><span class="sxs-lookup"><span data-stu-id="b876a-176">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="b876a-177">À l’instar d’un constructeur de type ( `static` ), il est garanti qu’il soit appelé une seule fois par un seul thread.</span><span class="sxs-lookup"><span data-stu-id="b876a-177">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="b876a-178">Recommandations</span><span class="sxs-lookup"><span data-stu-id="b876a-178">Recommendations</span></span>

- <span data-ttu-id="b876a-179">`async/await` et la `Task` résolution de service basée sur n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="b876a-179">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="b876a-180">Étant donné que C# ne prend pas en charge les constructeurs asynchrones, utilisez des méthodes asynchrones après la résolution synchrone du service.</span><span class="sxs-lookup"><span data-stu-id="b876a-180">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="b876a-181">Évitez de stocker des données et des configurations directement dans le conteneur de services.</span><span class="sxs-lookup"><span data-stu-id="b876a-181">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="b876a-182">Par exemple, le panier d’achat d’un utilisateur ne doit en général pas être ajouté au conteneur de services.</span><span class="sxs-lookup"><span data-stu-id="b876a-182">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="b876a-183">La configuration doit utiliser le modèle d’options.</span><span class="sxs-lookup"><span data-stu-id="b876a-183">Configuration should use the options pattern.</span></span> <span data-ttu-id="b876a-184">De même, évitez les objets « garde-données » qui existent uniquement pour autoriser l’accès à un autre objet.</span><span class="sxs-lookup"><span data-stu-id="b876a-184">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="b876a-185">Il est préférable de demander l’élément réel par le biais de l’injection de dépendance.</span><span class="sxs-lookup"><span data-stu-id="b876a-185">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="b876a-186">Évitez l’accès statique aux services.</span><span class="sxs-lookup"><span data-stu-id="b876a-186">Avoid static access to services.</span></span> <span data-ttu-id="b876a-187">Par exemple, évitez de capturer [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) en tant que champ ou propriété statique à utiliser ailleurs.</span><span class="sxs-lookup"><span data-stu-id="b876a-187">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="b876a-188">Conservez les fabriques DI en mode rapide et synchrone.</span><span class="sxs-lookup"><span data-stu-id="b876a-188">Keep DI factories fast and synchronous.</span></span>
- <span data-ttu-id="b876a-189">Évitez d’utiliser le *modèle de localisation de service*.</span><span class="sxs-lookup"><span data-stu-id="b876a-189">Avoid using the *service locator pattern*.</span></span> <span data-ttu-id="b876a-190">Par exemple, n’appelez pas <xref:System.IServiceProvider.GetService%2A> pour obtenir une instance de service lorsque vous pouvez utiliser l’injection de dépendance à la place.</span><span class="sxs-lookup"><span data-stu-id="b876a-190">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="b876a-191">Une autre variante du localisateur de service à éviter est l’injection d’une fabrique qui résout les dépendances au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b876a-191">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="b876a-192">Ces deux pratiques combinent des stratégies [Inversion de contrôle](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion).</span><span class="sxs-lookup"><span data-stu-id="b876a-192">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="b876a-193">Évitez les appels à <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> dans `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="b876a-193">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="b876a-194">L’appel de `BuildServiceProvider` se produit généralement lorsque le développeur souhaite résoudre un service dans `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="b876a-194">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="b876a-195">Les services transitoires jetables sont capturés par le conteneur pour la suppression.</span><span class="sxs-lookup"><span data-stu-id="b876a-195">Disposable transient services are captured by the container for disposal.</span></span> <span data-ttu-id="b876a-196">Cela peut entraîner une fuite de mémoire si elle est résolue à partir du conteneur de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="b876a-196">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="b876a-197">Activez la validation de l’étendue pour vous assurer que l’application n’a pas de singletons qui capturent les services délimités.</span><span class="sxs-lookup"><span data-stu-id="b876a-197">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="b876a-198">Pour plus d’informations, consultez [Validation de l’étendue](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="b876a-198">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="b876a-199">Comme pour toutes les recommandations, vous pouvez vous trouver dans des situations où il est nécessaire d’ignorer une recommandation.</span><span class="sxs-lookup"><span data-stu-id="b876a-199">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="b876a-200">Les exceptions sont rares, principalement des cas spéciaux dans l’infrastructure elle-même.</span><span class="sxs-lookup"><span data-stu-id="b876a-200">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="b876a-201">L’injection de dépendance constitue une *alternative* aux modèles d’accès aux objets statiques/globaux.</span><span class="sxs-lookup"><span data-stu-id="b876a-201">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="b876a-202">Il est possible que vous ne bénéficiez pas des avantages de l’injection de dépendances si vous la combinez avec l’accès aux objets statiques.</span><span class="sxs-lookup"><span data-stu-id="b876a-202">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="see-also"></a><span data-ttu-id="b876a-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b876a-203">See also</span></span>

- [<span data-ttu-id="b876a-204">Injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="b876a-204">Dependency injection in .NET</span></span>](dependency-injection.md)
