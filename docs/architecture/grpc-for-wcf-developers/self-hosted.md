---
title: Applications gRPC auto-hébergées - gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC en tant que services auto-hébergés.
ms.date: 09/02/2019
ms.openlocfilehash: 69f70e4077247fd07eba7abeee82f257dd1f4f90
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110904"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="ba9f2-103">Applications gRPC auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="ba9f2-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="ba9f2-104">Bien que ASP.NET applications Core 3.0 puissent être hébergées dans l’IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS parce qu’une partie de la fonctionnalité HTTP/2 n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="ba9f2-105">Cette fonctionnalité est un objectif pour une future mise à jour de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="ba9f2-106">Vous pouvez exécuter votre application en tant que service Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="ba9f2-107">Ou vous pouvez l’exécuter comme un service Linux contrôlé par [système](https://en.wikipedia.org/wiki/Systemd), en raison de nouvelles fonctionnalités dans les extensions d’hébergement .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="ba9f2-108">Exécutez votre application comme un service Windows</span><span class="sxs-lookup"><span data-stu-id="ba9f2-108">Run your app as a Windows service</span></span>

<span data-ttu-id="ba9f2-109">Pour configurer votre application ASP.NET Core pour fonctionner sous forme de service Windows, installez le forfait [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="ba9f2-110">Ensuite, ajoutez `UseWindowsService` un `CreateHostBuilder` appel `Program.cs`à la méthode en .</span><span class="sxs-lookup"><span data-stu-id="ba9f2-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="ba9f2-111">Si l’application n’est pas en `UseWindowsService` cours d’exécution comme un service Windows, la méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="ba9f2-112">Publiez maintenant votre application en utilisant l’une de ces méthodes :</span><span class="sxs-lookup"><span data-stu-id="ba9f2-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="ba9f2-113">De Visual Studio en cliquant à droite sur le projet et en sélectionnant **Publiez** sur le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="ba9f2-114">De la CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="ba9f2-115">Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du cadre* ou un déploiement *autonome.*</span><span class="sxs-lookup"><span data-stu-id="ba9f2-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="ba9f2-116">Les déploiements dépendants du cadre exigent que le temps de course partagé de base .NET soit installé sur l’hôte où ils sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="ba9f2-117">Les déploiements autonomes sont publiés avec une copie complète du temps d’exécution et du cadre .NET Core et peuvent être exécutés sur n’importe quel hôte.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="ba9f2-118">Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, consultez la documentation [de déploiement d’applications .NET Core.](../../core/deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="ba9f2-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="ba9f2-119">Pour publier une version autonome de l’application qui ne nécessite pas l’installation de l’heure d’exécution .NET Core 3.0 sur l’hôte, spécifiez l’heure d’exécution à inclure dans l’application.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="ba9f2-120">Utilisez `-r` le `--runtime`(ou) drapeau.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="ba9f2-121">Pour publier une construction dépendante du `-r` cadre, omettre le drapeau.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="ba9f2-122">Copiez le contenu `publish` complet de l’annuaire à un dossier d’installation.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="ba9f2-123">Ensuite, utilisez [l’outil sc](/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="ba9f2-124">Connectez-vous au journal de l’événement Windows</span><span class="sxs-lookup"><span data-stu-id="ba9f2-124">Log to the Windows event log</span></span>

<span data-ttu-id="ba9f2-125">La `UseWindowsService` méthode ajoute automatiquement un fournisseur [de connexion](/aspnet/core/fundamentals/logging/) qui écrit des messages journalaux au journal de l’événement Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="ba9f2-126">Vous pouvez configurer la connexion `EventLog` pour ce `Logging` fournisseur `appsettings.json` en ajoutant une entrée à la section ou à une autre source de configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="ba9f2-127">Vous pouvez remplacer le nom source utilisé dans `SourceName` le journal de l’événement en définissant une propriété dans ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="ba9f2-128">Si vous ne spécifiez pas un nom, le nom de l’application par défaut (normalement le nom d’assemblage exécutable) sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="ba9f2-129">Plus d’informations sur l’enregistrement est à la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="ba9f2-130">Exécutez votre application comme un service Linux avec</span><span class="sxs-lookup"><span data-stu-id="ba9f2-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="ba9f2-131">Pour configurer votre application ASP.NET Core pour fonctionner comme un service Linux (ou *daemon* dans le langage Linux), installez le paquet [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="ba9f2-132">Ensuite, ajoutez `UseSystemd` un `CreateHostBuilder` appel `Program.cs`à la méthode en .</span><span class="sxs-lookup"><span data-stu-id="ba9f2-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="ba9f2-133">Si l’application n’est pas en `UseSystemd` cours d’exécution comme un service Linux, la méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="ba9f2-134">Publiez maintenant votre demande.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-134">Now publish your application.</span></span> <span data-ttu-id="ba9f2-135">L’application peut être dépendante du cadre ou autonome pour l’exécution Linux pertinente (par exemple, `linux-x64`).</span><span class="sxs-lookup"><span data-stu-id="ba9f2-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="ba9f2-136">Vous pouvez publier en utilisant l’une de ces méthodes :</span><span class="sxs-lookup"><span data-stu-id="ba9f2-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="ba9f2-137">De Visual Studio en cliquant à droite sur le projet et en sélectionnant **Publiez** sur le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="ba9f2-138">De l’ERC de base .NET, en utilisant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ba9f2-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="ba9f2-139">Copiez le contenu `publish` complet de l’annuaire à un dossier d’installation sur l’hôte Linux.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="ba9f2-140">L’enregistrement du service nécessite un fichier spécial, appelé `/etc/systemd/system` *fichier unitaire,* à ajouter à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="ba9f2-141">Vous aurez besoin d’une autorisation de racine pour créer un fichier dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="ba9f2-142">Nommez le fichier avec `systemd` l’identifiant `.service` que vous souhaitez utiliser et l’extension.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="ba9f2-143">Par exemple, utilisez `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="ba9f2-144">Le fichier de service utilise le format INI, comme le montre cet exemple :</span><span class="sxs-lookup"><span data-stu-id="ba9f2-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="ba9f2-145">La `Type=notify` propriété `systemd` indique que l’application l’avisera sur le démarrage et l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="ba9f2-146">Le `WantedBy=multi-user.target` paramètre entraînera le démarrage du service lorsque le système Linux atteint le « niveau 2 », ce qui signifie qu’une coque multi-utilisateurs non graphique est active.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="ba9f2-147">Avant `systemd` de reconnaître le service, il doit recharger sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="ba9f2-148">Vous `systemd` contrôlez `systemctl` en utilisant la commande.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="ba9f2-149">Après le rechargement, `status` utilisez le sous-service pour confirmer que l’application s’est enregistrée avec succès.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="ba9f2-150">Si vous avez configuré correctement le service, vous obtiendrez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ba9f2-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="ba9f2-151">Utilisez `start` la commande pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="ba9f2-152">L’extension `.service` est facultative `systemctl start`lorsque vous utilisez .</span><span class="sxs-lookup"><span data-stu-id="ba9f2-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="ba9f2-153">Pour `systemd` vous dire de démarrer automatiquement le `enable` service sur le démarrage du système, utilisez la commande.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="ba9f2-154">Log à journald</span><span class="sxs-lookup"><span data-stu-id="ba9f2-154">Log to journald</span></span>

<span data-ttu-id="ba9f2-155">L’équivalent Linux du journal `journald`d’événements Windows est , un `systemd`service structuré de système de journalisation qui fait partie de .</span><span class="sxs-lookup"><span data-stu-id="ba9f2-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="ba9f2-156">Les messages journal écrits à la sortie standard `journald`par un daemon Linux sont automatiquement écrits à .</span><span class="sxs-lookup"><span data-stu-id="ba9f2-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="ba9f2-157">Pour configurer les niveaux `Console` d’enregistrement, utilisez la section de la configuration d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="ba9f2-158">La `UseSystemd` méthode du constructeur d’hôtes configure automatiquement le format de sortie de la console pour convenir au journal.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="ba9f2-159">Parce `journald` que c’est la norme pour les journaux Linux, une variété d’outils s’y intègrent.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="ba9f2-160">Vous pouvez facilement acheminer les journaux d’un `journald` système d’enregistrement externe.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="ba9f2-161">Travaillant localement sur l’hôte, `journalctl` vous pouvez utiliser la commande pour afficher les journaux depuis la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="ba9f2-162">Si vous disposez d’un environnement GUI disponible sur votre hôte, quelques internautes graphiques sont disponibles pour Linux, tels que *QJournalctl* et *gnome-logs*.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="ba9f2-163">Pour en savoir plus `systemd` sur la requête du `journalctl`journal de la ligne de commande en utilisant , voir [les pages d’homme](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="ba9f2-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="ba9f2-164">Certificats HTTPS pour les demandes auto-hébergées</span><span class="sxs-lookup"><span data-stu-id="ba9f2-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="ba9f2-165">Lorsque vous exécutez une demande de gRPC en production, vous devez utiliser un certificat TLS d’une autorité de certificat de confiance (CA).</span><span class="sxs-lookup"><span data-stu-id="ba9f2-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="ba9f2-166">Ce CA peut être un CA public, ou un CA interne pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="ba9f2-167">Sur les hôtes Windows, vous pouvez charger le <xref:System.Security.Cryptography.X509Certificates.X509Store> certificat à partir d’un magasin de [certificat](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé en utilisant la classe.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="ba9f2-168">Vous pouvez également `X509Store` utiliser la classe avec le magasin de clés OpenSSL sur certains hôtes Linux.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="ba9f2-169">Vous pouvez également créer des certificats en utilisant l’un des [constructeurs X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), à partir de l’un ou l’autre:</span><span class="sxs-lookup"><span data-stu-id="ba9f2-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="ba9f2-170">Un fichier, tel `.pfx` qu’un fichier protégé par un mot de passe fort</span><span class="sxs-lookup"><span data-stu-id="ba9f2-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="ba9f2-171">Données binaires récupérées à partir d’un service de stockage sécurisé tel [qu’Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="ba9f2-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="ba9f2-172">Vous pouvez configurer Kestrel pour utiliser un certificat de deux façons : de configuration ou de code.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="ba9f2-173">Définissez les certificats HTTPS en utilisant la configuration</span><span class="sxs-lookup"><span data-stu-id="ba9f2-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="ba9f2-174">L’approche de configuration nécessite `.pfx` de définir le chemin vers le fichier de certificat et le mot de passe dans la section configuration Kestrel.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="ba9f2-175">En `appsettings.json`, qui ressemblerait à ceci:</span><span class="sxs-lookup"><span data-stu-id="ba9f2-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="ba9f2-176">Fournissez le mot de passe en utilisant une source de configuration sécurisée comme Azure Key Vault ou Hashicorp Vault.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba9f2-177">Ne stockez pas de mots de passe non chiffrés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="ba9f2-178">Définissez les certificats HTTPS dans le code</span><span class="sxs-lookup"><span data-stu-id="ba9f2-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="ba9f2-179">Pour configurer HTTPS sur Kestrel `ConfigureKestrel` dans `IWebHostBuilder` le `Program` code, utilisez la méthode dans la classe.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="ba9f2-180">Encore une fois, assurez-vous `.pfx` de stocker le mot de passe pour le fichier et le récupérer à partir d’une source de configuration sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ba9f2-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba9f2-181">[Suivant précédent](grpc-in-production.md)
>[Next](docker.md)</span><span class="sxs-lookup"><span data-stu-id="ba9f2-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
