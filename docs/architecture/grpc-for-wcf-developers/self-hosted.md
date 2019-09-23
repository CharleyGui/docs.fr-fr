---
title: Applications gRPC auto-hébergées-gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC sous forme de services auto-hébergés.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184105"
---
# <a name="self-hosted-grpc-applications"></a>Applications gRPC auto-hébergées

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bien que les applications ASP.NET Core 3,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines fonctionnalités HTTP/2 ne sont pas encore prises en charge. Cette fonctionnalité est prévue dans une prochaine mise à jour de Windows Server.

Vous pouvez exécuter votre application en tant que service Windows, ou en tant que service Linux contrôlé par le [système](https://en.wikipedia.org/wiki/Systemd), grâce à de nouvelles fonctionnalités des extensions d’hébergement .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Exécuter votre application en tant que service Windows

Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Windows, installez le package [Microsoft. extensions. Hosting. services Windows,](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet. Ajoutez ensuite un appel à `UseWindowsService` à la `CreateHostBuilder` méthode dans `Program.cs`.

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
> Si l’application n’est pas exécutée en tant que `UseWindowsService` service Windows, la méthode ne fait rien.

À présent, publiez votre application, soit à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en sélectionnant *publier* dans le menu contextuel, soit à partir de la CLI .net core.

Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* . Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET Core sur l’hôte sur lequel ils sont exécutés. Les déploiements autonomes sont publiés avec une copie complète du runtime et du Framework .NET Core et peuvent être exécutés sur n’importe quel hôte. Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, reportez-vous à la documentation sur le [déploiement d’applications .net Core](https://docs.microsoft.com/dotnet/core/deploying/) .

Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .net Core 3,0 sur l’ordinateur hôte, spécifiez le runtime à inclure avec l’application à l’aide de `-r` l’indicateur `--runtime`(ou).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Pour publier une build dépendante de l’infrastructure `-r` , omettez l’indicateur.

```console
dotnet publish -c Release -o ./publish
```

Copiez le contenu complet du `publish` répertoire dans un dossier d’installation et utilisez l' [utilitaire SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour l’exécutable.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Journalisation dans le journal des événements Windows

La `UseWindowsService` méthode ajoute automatiquement un fournisseur de [journalisation](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) qui écrit des messages de journal dans le journal des événements Windows. Vous pouvez configurer la journalisation pour ce fournisseur en `EventLog` ajoutant une entrée `Logging` à la `appsettings.json` section de ou à une autre source de configuration. Vous pouvez remplacer le nom de la source utilisé dans le journal des événements `SourceName` en définissant une propriété dans ces paramètres. Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement le nom de l’assembly exécutable) sera utilisé.

Pour plus d’informations sur la journalisation, consultez la fin de ce chapitre.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Exécutez votre application en tant que service Linux avec SystemD

Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Linux (ou *démon* dans le jargon Linux), installez le package [Microsoft. extensions. Hosting. SYSTEMED](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) à partir de NuGet. Ajoutez ensuite un appel à `UseSystemd` à la `CreateHostBuilder` méthode dans `Program.cs`.

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
> Si l’application n’est pas exécutée en tant que `UseSystemd` service Linux, la méthode ne fait rien.

À présent, publiez votre application (dépendante de l’infrastructure ou autonome pour le runtime Linux concerné, `linux-x64`par exemple), à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en choisissant *publier* dans le menu contextuel, ou à partir de .net Interface CLI principale à l’aide de la commande suivante.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Copiez le contenu complet du `publish` répertoire dans un dossier d’installation sur l’hôte Linux. L’inscription du service nécessite l’ajout d’un fichier spécial, appelé « fichier d' `/etc/systemd/system` unité », au répertoire. Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier. Nommez le fichier avec l’identificateur que vous `systemd` souhaitez utiliser et l' `.service` extension. Par exemple, `/etc/systemd/system/myapp.service`.

Le fichier de service utilise le format INI, comme illustré dans cet exemple.

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

La `Type=notify` propriété indique `systemd` que l’application l’avertira au démarrage et à l’arrêt. Ce `WantedBy=multi-user.target` paramètre entraîne le démarrage du service lorsque le système Linux atteint « runlevel 2 », ce qui signifie qu’un interpréteur de commandes multi-utilisateur non graphique est actif.

Avant `systemd` de reconnaître le service, il doit recharger sa configuration. Vous contrôlez `systemd` à l' `systemctl` aide de la commande. Après le rechargement, utilisez `status` la sous-commande pour confirmer que l’application s’est correctement inscrite.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Si vous avez correctement configuré le service, la sortie suivante s’affiche :

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Utilisez la `start` commande pour démarrer le service.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> L' `.service` extension est facultative lors de `systemctl start`l’utilisation de.

Pour savoir `systemd` comment démarrer le service automatiquement au démarrage du système, utilisez `enable` la commande.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Consigner dans le journal

L’équivalent Linux du journal des événements Windows est `journald`, un service de système de journalisation structuré qui `systemd`fait partie de. Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement `journald`écrits, afin de configurer les niveaux de journalisation, utilisez la `Console` section de la configuration de la journalisation. La `UseSystemd` méthode du générateur d’ordinateur hôte configure automatiquement le format de sortie de la console pour l’adapter au journal.

Étant `journald` donné que est la norme pour les journaux Linux, il existe un large éventail d’outils qui s’intègrent avec elle et vous `journald` pouvez facilement acheminer les journaux de vers un système de journalisation externe. Travailler localement sur l’hôte, vous pouvez utiliser la `journalctl` commande pour afficher les journaux à partir de la ligne de commande.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.

Pour en savoir plus sur l’interrogation du journal système à partir de la `journalctl`ligne de commande avec, consultez [les pages man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificats HTTPs pour les applications auto-hébergées

Lors de l’exécution d’une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée. Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.

Sur les hôtes Windows, le certificat peut être chargé à partir d’un [magasin de certificats](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la [classe X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0). La `X509Store` classe peut également être utilisée avec le magasin de clés OpenSSL sur certains hôtes Linux.

Les certificats peuvent également être créés à l’aide de l’un des [constructeurs X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), soit à partir d’un `.pfx` fichier (par exemple, un fichier protégé par un mot de passe fort), soit à partir de données binaires récupérées à partir d’un service de stockage sécurisé tel que [Azure Key Vault ](https://azure.microsoft.com/services/key-vault/).

Kestrel peut être configuré pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.

### <a name="set-https-certificates-using-configuration"></a>Définir des certificats HTTPs à l’aide de la configuration

L’approche de configuration requiert la définition du chemin d' `.pfx` accès au fichier de certificat et du mot de passe dans la section de configuration Kestrel. Dans `appsettings.json` , cela ressemble à ceci.

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

Le mot de passe doit être fourni à l’aide d’une source de configuration sécurisée, par exemple Azure Key Vault ou Hashicorp Vault.

Vous ne devez pas stocker les mots de passe non chiffrés dans les fichiers de configuration.

### <a name="set-https-certificates-in-code"></a>Définir des certificats HTTPs dans le code

Pour configurer https sur Kestrel dans le code, utilisez `ConfigureKestrel` la méthode `IWebHostBuilder` sur dans `Program` la classe.

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

Là encore, le mot de `.pfx` passe du fichier doit être stocké dans et extrait d’une source de configuration sécurisée.

>[!div class="step-by-step"]
>[Précédent](grpc-in-production.md)
>[Suivant](docker.md)
