---
title: Nouveautés de .NET Core 2.2
description: Découvrez les nouvelles fonctionnalités de .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156580"
---
# <a name="whats-new-in-net-core-22"></a>Nouveautés de .NET Core 2.2

.NET Core 2.2 comporte des améliorations dans plusieurs domaines : déploiement d’applications, gestion des événements pour les services de runtime, authentification auprès des bases de données SQL Azure, performances du compilateur JIT et injection de code avant l’exécution de la méthode `Main`.

## <a name="new-deployment-mode"></a>Nouveau mode de déploiement

À partir de .NET Core 2.2, vous pouvez déployer des [exécutables dépendants du framework](../deploying/index.md#publish-runtime-dependent), qui sont des fichiers **.exe** au lieu de fichiers **.dll**. Comme les déploiements dépendants du framework, les exécutables dépendants du framework dépendent toujours de la présence d’une version de .NET Core partagée à l’échelle du système pour s’exécuter. Votre application ne comporte que votre code et les éventuelles dépendances tierces. Contrairement aux déploiements dépendants du framework, les exécutables dépendants du framework sont propres à la plateforme.

Ce nouveau mode de déploiement présente le net avantage de créer un exécutable au lieu d’une bibliothèque, ce qui permet d’exécuter directement l’application, sans appeler `dotnet` au préalable.

## <a name="core"></a>Core

**Gérer les événements dans les services de runtime**

Supposons que vous souhaitiez surveiller l’utilisation des services de runtime (par exemple, GC, JIT ou ThreadPool) par votre application, pour comprendre leur impact sur votre application.Sur les systèmes Windows, on effectue en général pour cela un monitoring des événements ETW du processus en cours.Bien que cette solution fonctionne toujours, il n’est pas toujours possible d’utiliser ETW, notamment dans un environnement à faibles privilèges ou sous Linux ou macOS.

À partir de .NET Core 2.2, la classe <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> peut consommer des événements CoreCLR. Ces événements décrivent le comportement de ces services de runtime, comme GC, JIT, ThreadPool et Interop. Ce sont les mêmes que dans le fournisseur ETW CoreCLR.Les applications peuvent ainsi consommer ces événements ou utiliser un mécanisme de transport pour les envoyer à un service d’agrégation de données de télémétrie. L’exemple de code suivant montre comment s’abonner aux événements :

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

Par ailleurs, .NET Core 2.2 ajoute les deux propriétés suivantes à la classe <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> pour fournir des informations supplémentaires sur les événements ETW :

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Données

**Authentification AAD à des bases de données SQL Azure avec la propriété SqlConnection.AccessToken**

À partir de .NET Core 2.2, il est possible d’utiliser un jeton d’accès émis par Azure Active Directory pour s’authentifier auprès d’une base de données SQL Azure. Pour prendre en charge les jetons d’accès, la propriété <xref:System.Data.SqlClient.SqlConnection.AccessToken> a été ajoutée à la classe <xref:System.Data.SqlClient.SqlConnection>. Téléchargez la version 4.6 du package NuGet System.Data.SqlClient afin de tirer parti de l’authentification AAD. Pour pouvoir utiliser la fonctionnalité, récupérez la valeur du jeton d’accès à l’aide de la [Bibliothèque d'authentification Active Directory pour .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contenue dans le package NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

## <a name="jit-compiler-improvements"></a>Améliorations du compilateur JIT

**La compilation hiérarchisée reste une fonctionnalité sur option**

Dans .NET Core 2.1, le compilateur JIT a implémenté une nouvelle technologie, la *compilation hiérarchisée*, que l’on peut choisir d’activer ou non. L’objectif de la compilation hiérarchisée est d’améliorer les performances. Une des tâches importantes effectuées par le compilateur JIT est l’optimisation de l’exécution du code. Pour les chemins de code peu utilisés cependant, le compilateur risque de passer plus de temps à optimiser le code que le runtime à exécuter du code non optimisé. La compilation à plusieurs niveaux ajoute deux étapes à la compilation JIT :

- Un **premier niveau**, qui génère du code aussi rapidement que possible.

- Un **second niveau**, qui génère un code optimisé pour les méthodes fréquemment exécutées. Le second niveau de compilation est effectué en parallèle pour améliorer les performances.

Pour plus d’informations sur l’amélioration des performances offerte par la compilation hiérarchisée, voir [Annonce de .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

Dans .NET Core 2.2 Preview 2, la compilation hiérarchisée était activée par défaut. Toutefois, nous avons décidé que nous ne sommes pas encore prêts à l’activer par défaut. C’est pourquoi, dans .NET Core 2.2, elle reste une fonctionnalité sur option. Pour plus d’informations sur le choix de la compilation hiérarchisée, voir [Amélioration du compilateur JIT](dotnet-core-2-1.md#jit-compiler-improvements) dans [Nouveautés de .NET Core 2.1](dotnet-core-2-1.md).

## <a name="runtime"></a>Runtime

**Injecter du code avant d’exécuter la méthode Main**

À partir de .NET Core 2.2, vous pouvez utiliser un hook de démarrage pour injecter du code avant d’exécuter la méthode Main d’une application. Les hooks de démarrage permettent à un hôte de personnaliser le comportement des applications une fois déployées, sans avoir à les recompiler ou à les modifier.

Nous attendons des fournisseurs d’hébergement qu’ils définissent la stratégie et la configuration personnalisées, y compris les paramètres susceptibles d’influencer le comportement du point d’entrée principal, et notamment le comportement de  <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> . Le hook peut être utilisé pour configurer l’injection de données de télémétrie ou de suivi, pour mettre en place des rappels à des fins de gestion ou pour définir un autre comportement dépendant de l’environnement. Il est distinct du point d’entrée, ce qui évite d’avoir à modifier le code utilisateur.

Pour plus d’informations, voir [Hook de démarrage hôte](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md).

## <a name="see-also"></a>Voir aussi

- [Nouveautés de .NET Core](index.md)
- [Nouveautés d’ASP.NET Core 2.2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nouvelles fonctionnalités d’EF Core 2.2](/ef/core/what-is-new/ef-core-2.2)
