---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937302"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hébergement : Redirection HTTPS activée pour les applications hors-processus DE l’IIS

La version 13.0.19218.0 du [module de base ASP.NET (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pour l’hébergement via l’IIE hors-processus permet une fonction de redirection HTTPS existante pour ASP.NET applications Core 3.0 et 2.2.

Pour discussion, voir [dotnet/AspNetCore 15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le modèle de projet ASP.NET Core 2.1 a d’abord <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>introduit le support pour les méthodes DE middleware HTTPS comme et . L’activation de la redirection HTTPS nécessitait l’ajout de configuration, car les applications en développement n’utilisent pas le port par défaut de 443. [HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) n’est actif que si la demande utilise déjà HTTPS. Localhost est ignoré par défaut.

#### <a name="new-behavior"></a>Nouveau comportement

Dans ASP.NET Core 3.0, le scénario HTTPS de l’IIS a été [amélioré.](https://github.com/dotnet/AspNetCore/pull/4685) Grâce à cette amélioration, une application pourrait découvrir `UseHttpsRedirection` les ports HTTPS du serveur et faire fonctionner par défaut. La composante en cours a `IServerAddresses` réalisé la découverte portuaire avec la fonctionnalité, qui n’affecte ASP.NET applications Core 3.0 parce que la bibliothèque en cours est version avec le cadre. Le composant hors-processus modifié pour `ASPNETCORE_HTTPS_PORT` ajouter automatiquement la variable de l’environnement. Ce changement a affecté les applications ASP.NET Core 2.2 et 3.0 parce que le composant hors-processus est partagé à l’échelle mondiale. ASP.NET les applications Core 2.1 ne sont pas affectées parce qu’elles utilisent une version antérieure d’ANCM par défaut.

Le comportement précédent a été modifié dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3 pour inverser les changements de comportement dans ASP.NET Core 2.x. Ces modifications n’affectent que les applications hors-processus DE l’IIS.

Comme indiqué ci-dessus, l’installation de ASP.NET Core 3.0.0 a `UseHttpsRedirection` eu pour effet secondaire d’activer également le middleware dans ASP.NET applications Core 2.x. Une modification a été apportée à l’ANCM dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3 de telle sorte que leur installation n’a plus cet effet sur ASP.NET applications Core 2.x. La `ASPNETCORE_HTTPS_PORT` variable d’environnement que l’ANCM a peuplée dans ASP.NET Core `ASPNETCORE_ANCM_HTTPS_PORT` 3.0.0 a été changée dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3. `UseHttpsRedirection`a également été mis à jour dans ces versions pour comprendre à la fois les nouvelles et les anciennes variables. ASP.NET Core 2.x ne sera pas mis à jour. En conséquence, il revient au comportement précédent d’être désactivé par défaut.

#### <a name="reason-for-change"></a>Raison du changement

Amélioration de la fonctionnalité ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise si vous voulez que tous les clients utilisent HTTPS. Pour permettre à certains clients d’utiliser HTTP, prenez l’une des étapes suivantes :

* Supprimez les `UseHttpsRedirection` `UseHsts` appels vers et `Startup.Configure` depuis la méthode de votre projet et redéploiez l’application.
* Dans votre fichier *web.config,* définissez la variable de l’environnement `ASPNETCORE_HTTPS_PORT` à une chaîne vide. Cette modification peut se produire directement sur le serveur sans redéployer l’application. Par exemple :

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`peut encore être:

* Activé manuellement dans ASP.NET Core 2.x `ASPNETCORE_HTTPS_PORT` en fixant la variable de l’environnement au numéro de port approprié (443 dans la plupart des scénarios de production).
* Désactivé dans ASP.NET Core 3.x en `ASPNETCORE_ANCM_HTTPS_PORT` définissant avec une valeur de chaîne vide. Cette valeur est définie de la `ASPNETCORE_HTTPS_PORT` même manière que l’exemple précédent.

Les machines fonctionnant ASP.NET applications Core 3.0.0 doivent installer le ASP.NET Core 3.0.1 runtime avant d’installer le ASP.NET Core 3.1.0 Aperçu 3 ANCM. Cela garantit que `UseHttpsRedirection` continue à fonctionner comme prévu pour les applications ASP.NET Core 3.0.

Dans Azure App Service, ANCM se déploie selon un calendrier distinct de l’exécution en raison de sa nature mondiale. L’ANCM a été déployée à Azure avec ces changements après ASP.NET Core 3.0.1 et 3.1.0 ont été déployés.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
