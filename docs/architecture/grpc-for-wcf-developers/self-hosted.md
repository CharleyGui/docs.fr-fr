---
title: Applications gRPC auto-hébergées-gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC sous forme de services auto-hébergés.
ms.date: 09/02/2019
ms.openlocfilehash: 00b4ad50eae629b5b36a890d1eecf7119386c74c
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545067"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="afda9-103">Applications gRPC auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="afda9-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="afda9-104">Bien que les applications ASP.NET Core 3,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines fonctionnalités HTTP/2 ne sont pas encore prises en charge.</span><span class="sxs-lookup"><span data-stu-id="afda9-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't yet supported.</span></span> <span data-ttu-id="afda9-105">Cette fonctionnalité est prévue dans une prochaine mise à jour de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="afda9-105">This functionality is expected in a future update to Windows Server.</span></span>

<span data-ttu-id="afda9-106">Vous pouvez exécuter votre application en tant que service Windows, ou en tant que service Linux contrôlé par le [système](https://en.wikipedia.org/wiki/Systemd), grâce à de nouvelles fonctionnalités des extensions d’hébergement .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="afda9-106">You can run your application as a Windows Service, or as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), thanks to some new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="afda9-107">Exécuter votre application en tant que service Windows</span><span class="sxs-lookup"><span data-stu-id="afda9-107">Run your app as a Windows service</span></span>

<span data-ttu-id="afda9-108">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Windows, installez le package [Microsoft. extensions. Hosting. services Windows,](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="afda9-108">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="afda9-109">Ajoutez ensuite un appel à `UseWindowsService` à la méthode `CreateHostBuilder` dans `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="afda9-109">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="afda9-110">Si l’application n’est pas exécutée en tant que service Windows, la méthode `UseWindowsService` ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="afda9-110">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="afda9-111">À présent, publiez votre application, soit à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en sélectionnant *publier* dans le menu contextuel, soit à partir de la CLI .net core.</span><span class="sxs-lookup"><span data-stu-id="afda9-111">Now publish your application, either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI.</span></span>

<span data-ttu-id="afda9-112">Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* .</span><span class="sxs-lookup"><span data-stu-id="afda9-112">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="afda9-113">Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET Core sur l’hôte sur lequel ils sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="afda9-113">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="afda9-114">Les déploiements autonomes sont publiés avec une copie complète du runtime et du Framework .NET Core et peuvent être exécutés sur n’importe quel hôte.</span><span class="sxs-lookup"><span data-stu-id="afda9-114">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="afda9-115">Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, reportez-vous à la documentation sur le [déploiement d’applications .net Core](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="afda9-115">For more information, including the advantages and disadvantages of each approach, refer to the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="afda9-116">Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .NET Core 3,0 sur l’ordinateur hôte, spécifiez le runtime à inclure avec l’application à l’aide de l’indicateur `-r` (ou `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="afda9-116">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application using the `-r` (or `--runtime`) flag.</span></span>

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="afda9-117">Pour publier une build dépendante de l’infrastructure, omettez l’indicateur `-r`.</span><span class="sxs-lookup"><span data-stu-id="afda9-117">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```console
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="afda9-118">Copiez le contenu complet du répertoire `publish` dans un dossier d’installation et utilisez l' [utilitaire SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="afda9-118">Copy the complete contents of the `publish` directory to an installation folder, and use the [sc utility](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a><span data-ttu-id="afda9-119">Journalisation dans le journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="afda9-119">Log to Windows Event Log</span></span>

<span data-ttu-id="afda9-120">La méthode `UseWindowsService` ajoute automatiquement un fournisseur de [journalisation](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) qui écrit des messages de journal dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="afda9-120">The `UseWindowsService` method automatically adds a [Logging](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) provider that writes log messages to the Windows Event Log.</span></span> <span data-ttu-id="afda9-121">Vous pouvez configurer la journalisation pour ce fournisseur en ajoutant une entrée `EventLog` à la section `Logging` de `appsettings.json` ou à une autre source de configuration.</span><span class="sxs-lookup"><span data-stu-id="afda9-121">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or other configuration source.</span></span> <span data-ttu-id="afda9-122">Vous pouvez remplacer le nom de la source utilisé dans le journal des événements en définissant une propriété `SourceName` dans ces paramètres. Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement, le nom de l’assembly exécutable) sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="afda9-122">The source name used in Event Log can be overridden by setting a `SourceName` property in these settings; if you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="afda9-123">Pour plus d’informations sur la journalisation, consultez la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="afda9-123">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="afda9-124">Exécutez votre application en tant que service Linux avec SystemD</span><span class="sxs-lookup"><span data-stu-id="afda9-124">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="afda9-125">Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Linux (ou *démon* dans le jargon Linux), installez le package [Microsoft. extensions. Hosting. SYSTEMED](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="afda9-125">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="afda9-126">Ajoutez ensuite un appel à `UseSystemd` à la méthode `CreateHostBuilder` dans `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="afda9-126">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="afda9-127">Si l’application n’est pas exécutée en tant que service Linux, la méthode `UseSystemd` ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="afda9-127">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="afda9-128">À présent, publiez votre application (dépendante de l’infrastructure ou autonome pour le runtime Linux approprié, par exemple, `linux-x64`), à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en sélectionnant *publier* dans le menu contextuel, ou à partir de la CLI .net core à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="afda9-128">Now publish your application (either framework-dependent, or self-contained for the relevant Linux runtime, for example, `linux-x64`), either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI using the following command.</span></span>

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

<span data-ttu-id="afda9-129">Copiez le contenu complet du répertoire `publish` dans un dossier d’installation sur l’hôte Linux.</span><span class="sxs-lookup"><span data-stu-id="afda9-129">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="afda9-130">L’inscription du service nécessite l’ajout d’un fichier spécial, appelé « fichier d’unité », au répertoire `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="afda9-130">Registering the service requires a special file, called a "unit file", to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="afda9-131">Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="afda9-131">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="afda9-132">Nommez le fichier avec l’identificateur que vous souhaitez `systemd` utiliser, ainsi que l’extension `.service`.</span><span class="sxs-lookup"><span data-stu-id="afda9-132">Name the file with the identifier you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="afda9-133">Par exemple, `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="afda9-133">For example, `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="afda9-134">Le fichier de service utilise le format INI, comme illustré dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="afda9-134">The service file uses INI format, as shown in this example.</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="afda9-135">La propriété `Type=notify` indique `systemd` que l’application l’avertira au démarrage et à l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="afda9-135">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="afda9-136">Le paramètre `WantedBy=multi-user.target` entraîne le démarrage du service lorsque le système Linux atteint « runlevel 2 », ce qui signifie qu’un interpréteur de commandes multi-utilisateur non graphique est actif.</span><span class="sxs-lookup"><span data-stu-id="afda9-136">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2", meaning a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="afda9-137">Avant que `systemd` ne reconnaisse le service, il doit recharger sa configuration.</span><span class="sxs-lookup"><span data-stu-id="afda9-137">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="afda9-138">Vous pouvez contrôler `systemd` à l’aide de la commande `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="afda9-138">You control `systemd` using the `systemctl` command.</span></span> <span data-ttu-id="afda9-139">Après le rechargement, utilisez la sous-commande `status` pour confirmer que l’application s’est correctement inscrite.</span><span class="sxs-lookup"><span data-stu-id="afda9-139">After reloading, use the `status` subcommand to confirm the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="afda9-140">Si vous avez correctement configuré le service, la sortie suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="afda9-140">If you've configured the service correctly, the following output will be shown:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="afda9-141">Utilisez la commande `start` pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="afda9-141">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="afda9-142">L’extension de `.service` est facultative lors de l’utilisation de `systemctl start`.</span><span class="sxs-lookup"><span data-stu-id="afda9-142">The `.service` extension is optional when using `systemctl start`.</span></span>

<span data-ttu-id="afda9-143">Pour indiquer à `systemd` de démarrer le service automatiquement au démarrage du système, utilisez la commande `enable`.</span><span class="sxs-lookup"><span data-stu-id="afda9-143">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="afda9-144">Consigner dans le journal</span><span class="sxs-lookup"><span data-stu-id="afda9-144">Log to journald</span></span>

<span data-ttu-id="afda9-145">L’équivalent Linux du journal des événements Windows est `journald`, un service de système de journalisation structuré qui fait partie de `systemd`.</span><span class="sxs-lookup"><span data-stu-id="afda9-145">The Linux equivalent of the Windows Event Log is `journald`, a structured logging system service that is part of `systemd`.</span></span> <span data-ttu-id="afda9-146">Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement écrits dans `journald`, afin de configurer les niveaux de journalisation, utilisez la section `Console` de la configuration de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="afda9-146">Log messages written to the standard output by a Linux daemon are automatically written to `journald`, so to configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="afda9-147">La méthode du générateur d’hôtes `UseSystemd` configure automatiquement le format de sortie de la console pour l’adapter au journal.</span><span class="sxs-lookup"><span data-stu-id="afda9-147">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="afda9-148">Étant donné que `journald` est la norme pour les journaux Linux, il existe un large éventail d’outils qui s’intègrent avec elle et vous pouvez facilement router les journaux d' `journald` vers un système de journalisation externe.</span><span class="sxs-lookup"><span data-stu-id="afda9-148">Because `journald` is the standard for Linux logs, there are a variety of tools that integrate with it, and you can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="afda9-149">Travailler localement sur l’hôte, vous pouvez utiliser la commande `journalctl` pour afficher les journaux à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="afda9-149">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="afda9-150">Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.</span><span class="sxs-lookup"><span data-stu-id="afda9-150">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="afda9-151">Pour en savoir plus sur l’interrogation du journal système à partir de la ligne de commande avec `journalctl`, consultez [les pages man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="afda9-151">To learn more about querying the systemd journal from the command line with `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="afda9-152">Certificats HTTPs pour les applications auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="afda9-152">HTTPS Certificates for self-hosted applications</span></span>

<span data-ttu-id="afda9-153">Lors de l’exécution d’une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="afda9-153">When running a gRPC application in production, you should use a TLS certificate from a trusted Certificate Authority (CA).</span></span> <span data-ttu-id="afda9-154">Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="afda9-154">This CA could be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="afda9-155">Sur les hôtes Windows, le certificat peut être chargé à partir d’un [magasin de certificats](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la classe <xref:System.Security.Cryptography.X509Certificates.X509Store>.</span><span class="sxs-lookup"><span data-stu-id="afda9-155">On Windows hosts, the certificate may be loaded from a secure [Certificate Store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="afda9-156">La classe `X509Store` peut également être utilisée avec le magasin de clés OpenSSL sur certains hôtes Linux.</span><span class="sxs-lookup"><span data-stu-id="afda9-156">The `X509Store` class can also be used with the OpenSSL key-store on some Linux hosts.</span></span>

<span data-ttu-id="afda9-157">Les certificats peuvent également être créés à l’aide de l’un des [constructeurs X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), soit à partir d’un fichier (par exemple, un fichier `.pfx` protégé par un mot de passe fort), soit à partir de données binaires récupérées à partir d’un service de stockage sécurisé tel que [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="afda9-157">Certificates may also be created using one of the [X509Certificate2 constructors](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), either from a file (for example a `.pfx` file protected by a strong password), or from binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="afda9-158">Kestrel peut être configuré pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="afda9-158">Kestrel can be configured to use a certificate in two ways: from configuration, or in code.</span></span>

### <a name="set-https-certificates-using-configuration"></a><span data-ttu-id="afda9-159">Définir des certificats HTTPs à l’aide de la configuration</span><span class="sxs-lookup"><span data-stu-id="afda9-159">Set HTTPS certificates using configuration</span></span>

<span data-ttu-id="afda9-160">L’approche de configuration requiert la définition du chemin d’accès au fichier de `.pfx` de certificat et du mot de passe dans la section de configuration Kestrel.</span><span class="sxs-lookup"><span data-stu-id="afda9-160">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="afda9-161">Dans `appsettings.json` qui ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="afda9-161">In `appsettings.json` that would look like this.</span></span>

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

<span data-ttu-id="afda9-162">Le mot de passe doit être fourni à l’aide d’une source de configuration sécurisée, par exemple Azure Key Vault ou Hashicorp Vault.</span><span class="sxs-lookup"><span data-stu-id="afda9-162">The password should be provided using a secure configuration source such as Azure KeyVault or Hashicorp Vault.</span></span>

<span data-ttu-id="afda9-163">Vous ne devez pas stocker les mots de passe non chiffrés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="afda9-163">You SHOULD NOT store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="afda9-164">Définir des certificats HTTPs dans le code</span><span class="sxs-lookup"><span data-stu-id="afda9-164">Set HTTPS certificates in code</span></span>

<span data-ttu-id="afda9-165">Pour configurer HTTPs sur Kestrel dans le code, utilisez la méthode `ConfigureKestrel` sur `IWebHostBuilder` dans la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="afda9-165">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="afda9-166">Là encore, le mot de passe du fichier de `.pfx` doit être stocké dans et extrait d’une source de configuration sécurisée.</span><span class="sxs-lookup"><span data-stu-id="afda9-166">Again, the password for the `.pfx` file should be stored in and retrieved from a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="afda9-167">[Précédent](grpc-in-production.md)
>[Suivant](docker.md)</span><span class="sxs-lookup"><span data-stu-id="afda9-167">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
