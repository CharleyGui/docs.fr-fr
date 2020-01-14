---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937302"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hébergement : redirection HTTPs activée pour les applications hors processus IIS

La version 13.0.19218.0 du [Module ASP.net Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pour l’hébergement via IIS Out-of-process active une fonctionnalité de REdirection https existante pour les applications ASP.net Core 3,0 et 2,2.

Pour plus d’informations, consultez [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le modèle de projet ASP.NET Core 2,1 a introduit d’abord la prise en charge des méthodes middleware HTTPs comme <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> et <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>. L’activation de la redirection HTTPs nécessitait l’ajout de la configuration, car les applications en développement n’utilisent pas le port par défaut 443. La [sécurité de transport strict http (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) est active uniquement si la demande utilise déjà le protocole HTTPS. Localhost est ignoré par défaut.

#### <a name="new-behavior"></a>Nouveau comportement

Dans ASP.NET Core 3,0, le scénario HTTPs IIS a été [amélioré](https://github.com/dotnet/AspNetCore/pull/4685). Avec l’amélioration, une application peut découvrir les ports HTTPs du serveur et rendre `UseHttpsRedirection` fonctionner par défaut. Le composant in-process a effectué la découverte du port avec la fonctionnalité `IServerAddresses`, qui affecte uniquement les applications ASP.NET Core 3,0, car la version de la bibliothèque in-process est gérée avec le Framework. Le composant out-of-process a changé pour ajouter automatiquement la variable d’environnement `ASPNETCORE_HTTPS_PORT`. Ce changement a affecté les applications ASP.NET Core 2,2 et 3,0, car le composant out-of-process est partagé globalement. Les applications ASP.NET Core 2,1 ne sont pas affectées, car elles utilisent une version antérieure de ANCM par défaut.

Le comportement précédent a été modifié dans ASP.NET Core 3.0.1 et 3.1.0 Preview 3 pour inverser les changements de comportement dans ASP.NET Core 2. x. Ces modifications affectent uniquement les applications hors processus IIS.

Comme indiqué ci-dessus, l’installation de ASP.NET Core 3.0.0 avait pour effet secondaire d’activer également l’intergiciel `UseHttpsRedirection` dans les applications ASP.NET Core 2. x. Une modification a été apportée à ANCM dans ASP.NET Core 3.0.1 et à la version préliminaire 3 de telle sorte que l’installation de ces derniers n’a plus d’effet sur les applications ASP.NET Core 2. x. La variable d’environnement `ASPNETCORE_HTTPS_PORT` qui ANCM remplie dans ASP.NET Core 3.0.0 a été remplacée par `ASPNETCORE_ANCM_HTTPS_PORT` dans ASP.NET Core 3.0.1 et 3.1.0 version préliminaire 3. `UseHttpsRedirection` a également été mis à jour dans ces versions pour comprendre les variables nouvelles et anciennes. ASP.NET Core 2. x ne sera pas mis à jour. Par conséquent, il revient au comportement précédent de la désactivation par défaut.

#### <a name="reason-for-change"></a>Motif de modification

Amélioration des fonctionnalités de ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise si vous souhaitez que tous les clients utilisent le protocole HTTPs. Pour permettre à certains clients d’utiliser le protocole HTTP, effectuez l’une des opérations suivantes :

* Supprimez les appels à `UseHttpsRedirection` et `UseHsts` à partir de la méthode de `Startup.Configure` de votre projet, puis redéployez l’application.
* Dans votre fichier *Web. config* , définissez la variable d’environnement `ASPNETCORE_HTTPS_PORT` sur une chaîne vide. Cette modification peut avoir lieu directement sur le serveur sans redéployer l’application. Par exemple :

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection` peut toujours être :

* Activé manuellement dans ASP.NET Core 2. x en affectant à la variable d’environnement `ASPNETCORE_HTTPS_PORT` le numéro de port approprié (443 dans la plupart des scénarios de production).
* Désactivé dans ASP.NET Core 3. x en définissant `ASPNETCORE_ANCM_HTTPS_PORT` avec une valeur de chaîne vide. Cette valeur est définie de la même façon que l’exemple précédent `ASPNETCORE_HTTPS_PORT`.

Les ordinateurs qui exécutent des applications ASP.NET Core 3.0.0 doivent installer le runtime ASP.NET Core 3.0.1 avant l’installation de l’ASP.NET Core de la version préliminaire 3 de ANCM. Cela garantit que `UseHttpsRedirection` continue à fonctionner comme prévu pour les applications ASP.NET Core 3,0.

Dans Azure App Service, ANCM déploie sur une planification distincte du runtime en raison de sa nature globale. ANCM a été déployé sur Azure avec ces modifications après le déploiement de ASP.NET Core 3.0.1 et 3.1.0.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
