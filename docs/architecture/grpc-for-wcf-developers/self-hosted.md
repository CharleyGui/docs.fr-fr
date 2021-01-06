---
title: Applications gRPC auto-hébergées-gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC sous forme de services auto-hébergés.
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938531"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="bab24-103">Applications gRPC auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="bab24-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="bab24-104">Bien que les applications ASP.NET Core 5,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines des fonctionnalités HTTP/2 ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bab24-104">Although ASP.NET Core 5.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="bab24-105">Cette fonctionnalité est un objectif pour une future mise à jour de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="bab24-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="bab24-106">Vous pouvez exécuter votre application en tant que service Windows.</span><span class="sxs-lookup"><span data-stu-id="bab24-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="bab24-107">Vous pouvez aussi l’exécuter en tant que service Linux contrôlé par [SystemD](https://en.wikipedia.org/wiki/Systemd), en raison de nouvelles fonctionnalités dans les extensions d’hébergement .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="bab24-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET 5.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="bab24-108">Exécuter votre application en tant que service Windows</span><span class="sxs-lookup"><span data-stu-id="bab24-108">Run your app as a Windows service</span></span>

<span data-ttu-id="bab24-109">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Windows, installez le package [Microsoft. extensions. Hosting. services Windows,](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="bab24-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="bab24-110">Ajoutez ensuite un appel à `UseWindowsService` à la `CreateHostBuilder` méthode dans `Program.cs` .</span><span class="sxs-lookup"><span data-stu-id="bab24-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="bab24-111">Si l’application n’est pas exécutée en tant que service Windows, la `UseWindowsService` méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="bab24-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="bab24-112">À présent, publiez votre application à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bab24-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="bab24-113">Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="bab24-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="bab24-114">À partir de l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="bab24-114">From the .NET CLI.</span></span>

<span data-ttu-id="bab24-115">Lorsque vous publiez une application .NET, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* .</span><span class="sxs-lookup"><span data-stu-id="bab24-115">When you publish a .NET application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="bab24-116">Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET sur l’hôte sur lequel ils sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="bab24-116">Framework-dependent deployments require the .NET Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="bab24-117">Les déploiements autonomes sont publiés avec une copie complète du runtime et du .NET Framework et peuvent être exécutés sur n’importe quel hôte.</span><span class="sxs-lookup"><span data-stu-id="bab24-117">Self-contained deployments are published with a complete copy of the .NET runtime and framework and can be run on any host.</span></span> <span data-ttu-id="bab24-118">Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, consultez la documentation relative au [déploiement d’applications .net](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="bab24-118">For more information, including the advantages and disadvantages of each approach, see the [.NET application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="bab24-119">Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .NET 5,0 sur l’ordinateur hôte, spécifiez le runtime à inclure dans l’application.</span><span class="sxs-lookup"><span data-stu-id="bab24-119">To publish a self-contained build of the application that does not require the .NET 5.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="bab24-120">Utilisez l' `-r` indicateur (ou `--runtime` ).</span><span class="sxs-lookup"><span data-stu-id="bab24-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="bab24-121">Pour publier une build dépendante de l’infrastructure, omettez l' `-r` indicateur.</span><span class="sxs-lookup"><span data-stu-id="bab24-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="bab24-122">Copiez le contenu complet du `publish` répertoire dans un dossier d’installation.</span><span class="sxs-lookup"><span data-stu-id="bab24-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="bab24-123">Utilisez ensuite l' [outil SC](/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="bab24-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="bab24-124">Consigner dans le journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="bab24-124">Log to the Windows event log</span></span>

<span data-ttu-id="bab24-125">La `UseWindowsService` méthode ajoute automatiquement un fournisseur de [journalisation](/aspnet/core/fundamentals/logging/) qui écrit des messages de journal dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="bab24-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="bab24-126">Vous pouvez configurer la journalisation pour ce fournisseur en ajoutant une `EventLog` entrée à la `Logging` section de `appsettings.json` ou une autre source de configuration.</span><span class="sxs-lookup"><span data-stu-id="bab24-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="bab24-127">Vous pouvez remplacer le nom de la source utilisé dans le journal des événements en définissant une `SourceName` propriété dans ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="bab24-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="bab24-128">Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement, le nom de l’assembly exécutable) sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="bab24-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="bab24-129">Pour plus d’informations sur la journalisation, consultez la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="bab24-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="bab24-130">Exécutez votre application en tant que service Linux avec SystemD</span><span class="sxs-lookup"><span data-stu-id="bab24-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="bab24-131">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Linux (ou *démon* dans le jargon Linux), installez le package [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="bab24-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="bab24-132">Ajoutez ensuite un appel à `UseSystemd` à la `CreateHostBuilder` méthode dans `Program.cs` .</span><span class="sxs-lookup"><span data-stu-id="bab24-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="bab24-133">Si l’application n’est pas exécutée en tant que service Linux, la `UseSystemd` méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="bab24-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="bab24-134">À présent, publiez votre application.</span><span class="sxs-lookup"><span data-stu-id="bab24-134">Now publish your application.</span></span> <span data-ttu-id="bab24-135">L’application peut être soit dépendante de l’infrastructure, soit autonome pour le runtime Linux concerné (par exemple, `linux-x64` ).</span><span class="sxs-lookup"><span data-stu-id="bab24-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="bab24-136">Vous pouvez publier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bab24-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="bab24-137">Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="bab24-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="bab24-138">À partir de l’interface CLI .NET, à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bab24-138">From the .NET CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="bab24-139">Copiez le contenu complet du `publish` répertoire dans un dossier d’installation sur l’hôte Linux.</span><span class="sxs-lookup"><span data-stu-id="bab24-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="bab24-140">L’inscription du service nécessite l’ajout d’un fichier spécial, appelé *fichier d’unité*, au `/etc/systemd/system` répertoire.</span><span class="sxs-lookup"><span data-stu-id="bab24-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="bab24-141">Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="bab24-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="bab24-142">Nommez le fichier avec l’identificateur que vous souhaitez `systemd` utiliser et l' `.service` extension.</span><span class="sxs-lookup"><span data-stu-id="bab24-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="bab24-143">Par exemple, utilisez `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="bab24-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="bab24-144">Le fichier de service utilise le format INI, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bab24-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="bab24-145">La `Type=notify` propriété indique `systemd` que l’application l’avertira au démarrage et à l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bab24-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="bab24-146">Ce `WantedBy=multi-user.target` paramètre entraîne le démarrage du service lorsque le système Linux atteint « runlevel 2 », ce qui signifie qu’un interpréteur de commandes multi-utilisateur non graphique est actif.</span><span class="sxs-lookup"><span data-stu-id="bab24-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="bab24-147">Avant `systemd` de reconnaître le service, il doit recharger sa configuration.</span><span class="sxs-lookup"><span data-stu-id="bab24-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="bab24-148">Vous pouvez contrôler `systemd` à l’aide de la `systemctl` commande.</span><span class="sxs-lookup"><span data-stu-id="bab24-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="bab24-149">Après le rechargement, utilisez la sous- `status` commande pour confirmer que l’application s’est correctement inscrite.</span><span class="sxs-lookup"><span data-stu-id="bab24-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="bab24-150">Si vous avez correctement configuré le service, vous obtiendrez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bab24-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="bab24-151">Utilisez la `start` commande pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="bab24-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="bab24-152">L' `.service` extension est facultative lorsque vous utilisez `systemctl start` .</span><span class="sxs-lookup"><span data-stu-id="bab24-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="bab24-153">Pour savoir `systemd` Comment démarrer le service automatiquement au démarrage du système, utilisez la `enable` commande.</span><span class="sxs-lookup"><span data-stu-id="bab24-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="bab24-154">Consigner dans le journal</span><span class="sxs-lookup"><span data-stu-id="bab24-154">Log to journald</span></span>

<span data-ttu-id="bab24-155">L’équivalent Linux du journal des événements Windows est `journald` , un service de système de journalisation structuré qui fait partie de `systemd` .</span><span class="sxs-lookup"><span data-stu-id="bab24-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="bab24-156">Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement écrits dans `journald` .</span><span class="sxs-lookup"><span data-stu-id="bab24-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="bab24-157">Pour configurer les niveaux de journalisation, utilisez la `Console` section de la configuration de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="bab24-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="bab24-158">La `UseSystemd` méthode du générateur d’ordinateur hôte configure automatiquement le format de sortie de la console pour l’adapter au journal.</span><span class="sxs-lookup"><span data-stu-id="bab24-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="bab24-159">Étant donné que `journald` est la norme pour les journaux Linux, un large éventail d’outils s’intègre au service informatique.</span><span class="sxs-lookup"><span data-stu-id="bab24-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="bab24-160">Vous pouvez facilement acheminer les journaux de `journald` vers un système de journalisation externe.</span><span class="sxs-lookup"><span data-stu-id="bab24-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="bab24-161">Travailler localement sur l’hôte, vous pouvez utiliser la `journalctl` commande pour afficher les journaux à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bab24-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="bab24-162">Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.</span><span class="sxs-lookup"><span data-stu-id="bab24-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="bab24-163">Pour en savoir plus sur l’interrogation du `systemd` Journal à partir de la ligne de commande à l’aide de `journalctl` , consultez [manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="bab24-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="bab24-164">Certificats HTTPs pour les applications auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="bab24-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="bab24-165">Lorsque vous exécutez une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="bab24-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="bab24-166">Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="bab24-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="bab24-167">Sur les hôtes Windows, vous pouvez charger le certificat à partir d’un [magasin de certificats](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la <xref:System.Security.Cryptography.X509Certificates.X509Store> classe.</span><span class="sxs-lookup"><span data-stu-id="bab24-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="bab24-168">Vous pouvez également utiliser la `X509Store` classe avec le magasin de clés OpenSSL sur certains hôtes Linux.</span><span class="sxs-lookup"><span data-stu-id="bab24-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="bab24-169">Vous pouvez également créer des certificats à l’aide de l’un des [constructeurs X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), à partir des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="bab24-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="bab24-170">Un fichier, tel qu’un `.pfx` fichier protégé par un mot de passe fort</span><span class="sxs-lookup"><span data-stu-id="bab24-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="bab24-171">Données binaires récupérées à partir d’un service de stockage sécurisé, par exemple [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="bab24-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="bab24-172">Vous pouvez configurer Kestrel pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="bab24-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="bab24-173">Définir des certificats HTTPs à l’aide de la configuration</span><span class="sxs-lookup"><span data-stu-id="bab24-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="bab24-174">L’approche de configuration requiert la définition du chemin d’accès au fichier de certificat `.pfx` et du mot de passe dans la section de configuration Kestrel.</span><span class="sxs-lookup"><span data-stu-id="bab24-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="bab24-175">Dans `appsettings.json` , cela ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="bab24-175">In `appsettings.json`, that would look like this:</span></span>

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

<span data-ttu-id="bab24-176">Fournissez le mot de passe à l’aide d’une source de configuration sécurisée telle que Azure Key Vault ou le coffre Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="bab24-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bab24-177">Ne stockez pas les mots de passe non chiffrés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="bab24-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="bab24-178">Définir des certificats HTTPs dans le code</span><span class="sxs-lookup"><span data-stu-id="bab24-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="bab24-179">Pour configurer HTTPs sur Kestrel dans le code, utilisez la `ConfigureKestrel` méthode sur `IWebHostBuilder` dans la `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="bab24-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

<span data-ttu-id="bab24-180">Là encore, veillez à stocker le mot de passe du `.pfx` fichier dans et à le récupérer à partir d’une source de configuration sécurisée.</span><span class="sxs-lookup"><span data-stu-id="bab24-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bab24-181">[Précédent](grpc-in-production.md) 
> [Suivant](docker.md)</span><span class="sxs-lookup"><span data-stu-id="bab24-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
