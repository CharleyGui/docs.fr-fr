---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937302"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="11adb-101">Hébergement : Redirection HTTPS activée pour les applications hors-processus DE l’IIS</span><span class="sxs-lookup"><span data-stu-id="11adb-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="11adb-102">La version 13.0.19218.0 du [module de base ASP.NET (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pour l’hébergement via l’IIE hors-processus permet une fonction de redirection HTTPS existante pour ASP.NET applications Core 3.0 et 2.2.</span><span class="sxs-lookup"><span data-stu-id="11adb-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="11adb-103">Pour discussion, voir [dotnet/AspNetCore 15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="11adb-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="11adb-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="11adb-104">Version introduced</span></span>

<span data-ttu-id="11adb-105">3.0</span><span class="sxs-lookup"><span data-stu-id="11adb-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="11adb-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="11adb-106">Old behavior</span></span>

<span data-ttu-id="11adb-107">Le modèle de projet ASP.NET Core 2.1 a d’abord <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>introduit le support pour les méthodes DE middleware HTTPS comme et .</span><span class="sxs-lookup"><span data-stu-id="11adb-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="11adb-108">L’activation de la redirection HTTPS nécessitait l’ajout de configuration, car les applications en développement n’utilisent pas le port par défaut de 443.</span><span class="sxs-lookup"><span data-stu-id="11adb-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="11adb-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) n’est actif que si la demande utilise déjà HTTPS.</span><span class="sxs-lookup"><span data-stu-id="11adb-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="11adb-110">Localhost est ignoré par défaut.</span><span class="sxs-lookup"><span data-stu-id="11adb-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="11adb-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="11adb-111">New behavior</span></span>

<span data-ttu-id="11adb-112">Dans ASP.NET Core 3.0, le scénario HTTPS de l’IIS a été [amélioré.](https://github.com/dotnet/AspNetCore/pull/4685)</span><span class="sxs-lookup"><span data-stu-id="11adb-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="11adb-113">Grâce à cette amélioration, une application pourrait découvrir `UseHttpsRedirection` les ports HTTPS du serveur et faire fonctionner par défaut.</span><span class="sxs-lookup"><span data-stu-id="11adb-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="11adb-114">La composante en cours a `IServerAddresses` réalisé la découverte portuaire avec la fonctionnalité, qui n’affecte ASP.NET applications Core 3.0 parce que la bibliothèque en cours est version avec le cadre.</span><span class="sxs-lookup"><span data-stu-id="11adb-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="11adb-115">Le composant hors-processus modifié pour `ASPNETCORE_HTTPS_PORT` ajouter automatiquement la variable de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="11adb-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="11adb-116">Ce changement a affecté les applications ASP.NET Core 2.2 et 3.0 parce que le composant hors-processus est partagé à l’échelle mondiale.</span><span class="sxs-lookup"><span data-stu-id="11adb-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="11adb-117">ASP.NET les applications Core 2.1 ne sont pas affectées parce qu’elles utilisent une version antérieure d’ANCM par défaut.</span><span class="sxs-lookup"><span data-stu-id="11adb-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="11adb-118">Le comportement précédent a été modifié dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3 pour inverser les changements de comportement dans ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="11adb-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="11adb-119">Ces modifications n’affectent que les applications hors-processus DE l’IIS.</span><span class="sxs-lookup"><span data-stu-id="11adb-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="11adb-120">Comme indiqué ci-dessus, l’installation de ASP.NET Core 3.0.0 a `UseHttpsRedirection` eu pour effet secondaire d’activer également le middleware dans ASP.NET applications Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="11adb-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="11adb-121">Une modification a été apportée à l’ANCM dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3 de telle sorte que leur installation n’a plus cet effet sur ASP.NET applications Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="11adb-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="11adb-122">La `ASPNETCORE_HTTPS_PORT` variable d’environnement que l’ANCM a peuplée dans ASP.NET Core `ASPNETCORE_ANCM_HTTPS_PORT` 3.0.0 a été changée dans ASP.NET Core 3.0.1 et 3.1.0 Aperçu 3.</span><span class="sxs-lookup"><span data-stu-id="11adb-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="11adb-123">`UseHttpsRedirection`a également été mis à jour dans ces versions pour comprendre à la fois les nouvelles et les anciennes variables.</span><span class="sxs-lookup"><span data-stu-id="11adb-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="11adb-124">ASP.NET Core 2.x ne sera pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="11adb-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="11adb-125">En conséquence, il revient au comportement précédent d’être désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="11adb-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="11adb-126">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="11adb-126">Reason for change</span></span>

<span data-ttu-id="11adb-127">Amélioration de la fonctionnalité ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="11adb-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="11adb-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="11adb-128">Recommended action</span></span>

<span data-ttu-id="11adb-129">Aucune action n’est requise si vous voulez que tous les clients utilisent HTTPS.</span><span class="sxs-lookup"><span data-stu-id="11adb-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="11adb-130">Pour permettre à certains clients d’utiliser HTTP, prenez l’une des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="11adb-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="11adb-131">Supprimez les `UseHttpsRedirection` `UseHsts` appels vers et `Startup.Configure` depuis la méthode de votre projet et redéploiez l’application.</span><span class="sxs-lookup"><span data-stu-id="11adb-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="11adb-132">Dans votre fichier *web.config,* définissez la variable de l’environnement `ASPNETCORE_HTTPS_PORT` à une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="11adb-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="11adb-133">Cette modification peut se produire directement sur le serveur sans redéployer l’application.</span><span class="sxs-lookup"><span data-stu-id="11adb-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="11adb-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="11adb-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="11adb-135">`UseHttpsRedirection`peut encore être:</span><span class="sxs-lookup"><span data-stu-id="11adb-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="11adb-136">Activé manuellement dans ASP.NET Core 2.x `ASPNETCORE_HTTPS_PORT` en fixant la variable de l’environnement au numéro de port approprié (443 dans la plupart des scénarios de production).</span><span class="sxs-lookup"><span data-stu-id="11adb-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="11adb-137">Désactivé dans ASP.NET Core 3.x en `ASPNETCORE_ANCM_HTTPS_PORT` définissant avec une valeur de chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="11adb-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="11adb-138">Cette valeur est définie de la `ASPNETCORE_HTTPS_PORT` même manière que l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="11adb-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="11adb-139">Les machines fonctionnant ASP.NET applications Core 3.0.0 doivent installer le ASP.NET Core 3.0.1 runtime avant d’installer le ASP.NET Core 3.1.0 Aperçu 3 ANCM.</span><span class="sxs-lookup"><span data-stu-id="11adb-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="11adb-140">Cela garantit que `UseHttpsRedirection` continue à fonctionner comme prévu pour les applications ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="11adb-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="11adb-141">Dans Azure App Service, ANCM se déploie selon un calendrier distinct de l’exécution en raison de sa nature mondiale.</span><span class="sxs-lookup"><span data-stu-id="11adb-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="11adb-142">L’ANCM a été déployée à Azure avec ces changements après ASP.NET Core 3.0.1 et 3.1.0 ont été déployés.</span><span class="sxs-lookup"><span data-stu-id="11adb-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="11adb-143">Category</span><span class="sxs-lookup"><span data-stu-id="11adb-143">Category</span></span>

<span data-ttu-id="11adb-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="11adb-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11adb-145">API affectées</span><span class="sxs-lookup"><span data-stu-id="11adb-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
