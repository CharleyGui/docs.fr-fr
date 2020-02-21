---
title: Applications gRPC auto-hébergées-gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC sous forme de services auto-hébergés.
ms.date: 09/02/2019
ms.openlocfilehash: ee370ba1893b060505b38ddf84235bd84433ad32
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542987"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="53119-103">Applications gRPC auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="53119-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="53119-104">Bien que les applications ASP.NET Core 3,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines des fonctionnalités HTTP/2 ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="53119-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="53119-105">Cette fonctionnalité est un objectif pour une future mise à jour de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="53119-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="53119-106">Vous pouvez exécuter votre application en tant que service Windows.</span><span class="sxs-lookup"><span data-stu-id="53119-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="53119-107">Vous pouvez aussi l’exécuter en tant que service Linux contrôlé par [SystemD](https://en.wikipedia.org/wiki/Systemd), en raison des nouvelles fonctionnalités des extensions d’hébergement .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="53119-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="53119-108">Exécuter votre application en tant que service Windows</span><span class="sxs-lookup"><span data-stu-id="53119-108">Run your app as a Windows service</span></span>

<span data-ttu-id="53119-109">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Windows, installez le package [Microsoft. extensions. Hosting. services Windows,](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="53119-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="53119-110">Ajoutez ensuite un appel à `UseWindowsService` à la méthode `CreateHostBuilder` dans `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="53119-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="53119-111">Si l’application n’est pas exécutée en tant que service Windows, la méthode `UseWindowsService` ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="53119-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="53119-112">À présent, publiez votre application à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="53119-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="53119-113">Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="53119-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="53119-114">À partir de la CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53119-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="53119-115">Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* .</span><span class="sxs-lookup"><span data-stu-id="53119-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="53119-116">Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET Core sur l’hôte sur lequel ils sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="53119-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="53119-117">Les déploiements autonomes sont publiés avec une copie complète du runtime et du Framework .NET Core et peuvent être exécutés sur n’importe quel hôte.</span><span class="sxs-lookup"><span data-stu-id="53119-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="53119-118">Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, consultez la documentation sur le [déploiement d’applications .net Core](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="53119-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="53119-119">Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .NET Core 3,0 sur l’ordinateur hôte, spécifiez le runtime à inclure dans l’application.</span><span class="sxs-lookup"><span data-stu-id="53119-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="53119-120">Utilisez l’indicateur `-r` (ou `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="53119-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="53119-121">Pour publier une build dépendante de l’infrastructure, omettez l’indicateur `-r`.</span><span class="sxs-lookup"><span data-stu-id="53119-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="53119-122">Copiez le contenu complet du répertoire `publish` dans un dossier d’installation.</span><span class="sxs-lookup"><span data-stu-id="53119-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="53119-123">Utilisez ensuite l' [outil SC](/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="53119-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="53119-124">Consigner dans le journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="53119-124">Log to the Windows event log</span></span>

<span data-ttu-id="53119-125">La méthode `UseWindowsService` ajoute automatiquement un fournisseur de [journalisation](/aspnet/core/fundamentals/logging/) qui écrit des messages de journal dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="53119-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="53119-126">Vous pouvez configurer la journalisation pour ce fournisseur en ajoutant une entrée `EventLog` à la section `Logging` de `appsettings.json` ou une autre source de configuration.</span><span class="sxs-lookup"><span data-stu-id="53119-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span> 

<span data-ttu-id="53119-127">Vous pouvez remplacer le nom de la source utilisé dans le journal des événements en définissant une propriété de `SourceName` dans ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="53119-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="53119-128">Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement, le nom de l’assembly exécutable) sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="53119-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="53119-129">Pour plus d’informations sur la journalisation, consultez la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="53119-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="53119-130">Exécutez votre application en tant que service Linux avec SystemD</span><span class="sxs-lookup"><span data-stu-id="53119-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="53119-131">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Linux (ou *démon* dans le jargon Linux), installez le package [Microsoft. extensions. Hosting. SYSTEMED](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="53119-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="53119-132">Ajoutez ensuite un appel à `UseSystemd` à la méthode `CreateHostBuilder` dans `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="53119-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="53119-133">Si l’application n’est pas exécutée en tant que service Linux, la méthode `UseSystemd` ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="53119-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="53119-134">À présent, publiez votre application.</span><span class="sxs-lookup"><span data-stu-id="53119-134">Now publish your application.</span></span> <span data-ttu-id="53119-135">L’application peut être soit dépendante de l’infrastructure, soit autonome pour le runtime Linux concerné (par exemple, `linux-x64`).</span><span class="sxs-lookup"><span data-stu-id="53119-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="53119-136">Vous pouvez publier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="53119-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="53119-137">Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="53119-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span> 
* <span data-ttu-id="53119-138">À partir de la CLI .NET Core, à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="53119-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="53119-139">Copiez le contenu complet du répertoire `publish` dans un dossier d’installation sur l’hôte Linux.</span><span class="sxs-lookup"><span data-stu-id="53119-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="53119-140">L’inscription du service nécessite l’ajout d’un fichier spécial, appelé *fichier d’unité*, au répertoire `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="53119-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="53119-141">Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="53119-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="53119-142">Nommez le fichier avec l’identificateur que vous souhaitez `systemd` utiliser, ainsi que l’extension `.service`.</span><span class="sxs-lookup"><span data-stu-id="53119-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="53119-143">Par exemple, utilisez `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="53119-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="53119-144">Le fichier de service utilise le format INI, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="53119-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="53119-145">La propriété `Type=notify` indique `systemd` que l’application l’avertira au démarrage et à l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="53119-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="53119-146">Le paramètre `WantedBy=multi-user.target` entraîne le démarrage du service lorsque le système Linux atteint « runlevel 2 », ce qui signifie qu’un interpréteur de commandes multi-utilisateur non graphique est actif.</span><span class="sxs-lookup"><span data-stu-id="53119-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="53119-147">Avant que `systemd` ne reconnaisse le service, il doit recharger sa configuration.</span><span class="sxs-lookup"><span data-stu-id="53119-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="53119-148">Vous pouvez contrôler `systemd` à l’aide de la commande `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="53119-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="53119-149">Après le rechargement, utilisez la sous-commande `status` pour vérifier que l’application s’est correctement inscrite.</span><span class="sxs-lookup"><span data-stu-id="53119-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="53119-150">Si vous avez correctement configuré le service, vous obtiendrez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="53119-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="53119-151">Utilisez la commande `start` pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="53119-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="53119-152">L’extension de `.service` est facultative lorsque vous utilisez `systemctl start`.</span><span class="sxs-lookup"><span data-stu-id="53119-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="53119-153">Pour indiquer à `systemd` de démarrer le service automatiquement au démarrage du système, utilisez la commande `enable`.</span><span class="sxs-lookup"><span data-stu-id="53119-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="53119-154">Consigner dans le journal</span><span class="sxs-lookup"><span data-stu-id="53119-154">Log to journald</span></span>

<span data-ttu-id="53119-155">L’équivalent Linux du journal des événements Windows est `journald`, un service de système de journalisation structuré qui fait partie de `systemd`.</span><span class="sxs-lookup"><span data-stu-id="53119-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="53119-156">Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement écrits dans `journald`.</span><span class="sxs-lookup"><span data-stu-id="53119-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="53119-157">Pour configurer les niveaux de journalisation, utilisez la section `Console` de la configuration de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="53119-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="53119-158">La méthode du générateur d’hôtes `UseSystemd` configure automatiquement le format de sortie de la console pour l’adapter au journal.</span><span class="sxs-lookup"><span data-stu-id="53119-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="53119-159">Étant donné que `journald` est la norme pour les journaux Linux, un large éventail d’outils s’y intègre.</span><span class="sxs-lookup"><span data-stu-id="53119-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="53119-160">Vous pouvez facilement acheminer les journaux de `journald` vers un système de journalisation externe.</span><span class="sxs-lookup"><span data-stu-id="53119-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="53119-161">Travailler localement sur l’hôte, vous pouvez utiliser la commande `journalctl` pour afficher les journaux à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53119-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="53119-162">Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.</span><span class="sxs-lookup"><span data-stu-id="53119-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="53119-163">Pour en savoir plus sur l’interrogation du journal `systemd` à partir de la ligne de commande à l’aide de `journalctl`, consultez [les pages man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="53119-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="53119-164">Certificats HTTPs pour les applications auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="53119-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="53119-165">Lorsque vous exécutez une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="53119-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="53119-166">Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="53119-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="53119-167">Sur les hôtes Windows, vous pouvez charger le certificat à partir d’un [magasin de certificats](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la classe <xref:System.Security.Cryptography.X509Certificates.X509Store>.</span><span class="sxs-lookup"><span data-stu-id="53119-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="53119-168">Vous pouvez également utiliser la classe `X509Store` avec le magasin de clés OpenSSL sur certains hôtes Linux.</span><span class="sxs-lookup"><span data-stu-id="53119-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="53119-169">Vous pouvez également créer des certificats à l’aide de l’un des [constructeurs X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), à partir des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="53119-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="53119-170">Un fichier, tel qu’un fichier `.pfx` protégé par un mot de passe fort</span><span class="sxs-lookup"><span data-stu-id="53119-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="53119-171">Données binaires récupérées à partir d’un service de stockage sécurisé, par exemple [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="53119-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="53119-172">Vous pouvez configurer Kestrel pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="53119-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="53119-173">Définir des certificats HTTPs à l’aide de la configuration</span><span class="sxs-lookup"><span data-stu-id="53119-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="53119-174">L’approche de configuration requiert la définition du chemin d’accès au fichier de `.pfx` de certificat et du mot de passe dans la section de configuration Kestrel.</span><span class="sxs-lookup"><span data-stu-id="53119-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="53119-175">Dans `appsettings.json`, cela ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="53119-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="53119-176">Fournissez le mot de passe à l’aide d’une source de configuration sécurisée telle que Azure Key Vault ou le coffre Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="53119-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53119-177">Ne stockez pas les mots de passe non chiffrés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="53119-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="53119-178">Définir des certificats HTTPs dans le code</span><span class="sxs-lookup"><span data-stu-id="53119-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="53119-179">Pour configurer HTTPs sur Kestrel dans le code, utilisez la méthode `ConfigureKestrel` sur `IWebHostBuilder` dans la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="53119-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="53119-180">Là encore, veillez à stocker le mot de passe pour le fichier `.pfx` dans et à le récupérer à partir d’une source de configuration sécurisée.</span><span class="sxs-lookup"><span data-stu-id="53119-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53119-181">[Précédent](grpc-in-production.md)
>[Suivant](docker.md)</span><span class="sxs-lookup"><span data-stu-id="53119-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
