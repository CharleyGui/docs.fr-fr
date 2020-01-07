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
# <a name="self-hosted-grpc-applications"></a>Applications gRPC auto-hébergées

Bien que les applications ASP.NET Core 3,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines fonctionnalités HTTP/2 ne sont pas encore prises en charge. Cette fonctionnalité est prévue dans une prochaine mise à jour de Windows Server.

Vous pouvez exécuter votre application en tant que service Windows, ou en tant que service Linux contrôlé par le [système](https://en.wikipedia.org/wiki/Systemd), grâce à de nouvelles fonctionnalités des extensions d’hébergement .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Exécuter votre application en tant que service Windows

Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Windows, installez le package [Microsoft. extensions. Hosting. services Windows,](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet. Ajoutez ensuite un appel à `UseWindowsService` à la méthode `CreateHostBuilder` dans `Program.cs`.

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
> Si l’application n’est pas exécutée en tant que service Windows, la méthode `UseWindowsService` ne fait rien.

À présent, publiez votre application, soit à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en sélectionnant *publier* dans le menu contextuel, soit à partir de la CLI .net core.

Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* . Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET Core sur l’hôte sur lequel ils sont exécutés. Les déploiements autonomes sont publiés avec une copie complète du runtime et du Framework .NET Core et peuvent être exécutés sur n’importe quel hôte. Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, reportez-vous à la documentation sur le [déploiement d’applications .net Core](../../core/deploying/index.md) .

Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .NET Core 3,0 sur l’ordinateur hôte, spécifiez le runtime à inclure avec l’application à l’aide de l’indicateur `-r` (ou `--runtime`).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Pour publier une build dépendante de l’infrastructure, omettez l’indicateur `-r`.

```console
dotnet publish -c Release -o ./publish
```

Copiez le contenu complet du répertoire `publish` dans un dossier d’installation et utilisez l' [utilitaire SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour l’exécutable.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Journalisation dans le journal des événements Windows

La méthode `UseWindowsService` ajoute automatiquement un fournisseur de [journalisation](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) qui écrit des messages de journal dans le journal des événements Windows. Vous pouvez configurer la journalisation pour ce fournisseur en ajoutant une entrée `EventLog` à la section `Logging` de `appsettings.json` ou à une autre source de configuration. Vous pouvez remplacer le nom de la source utilisé dans le journal des événements en définissant une propriété `SourceName` dans ces paramètres. Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement, le nom de l’assembly exécutable) sera utilisé.

Pour plus d’informations sur la journalisation, consultez la fin de ce chapitre.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Exécutez votre application en tant que service Linux avec SystemD

Pour configurer votre application ASP.NET Core pour qu’elle s’exécute en tant que service Linux (ou *démon* dans le jargon Linux), installez le package [Microsoft. extensions. Hosting. SYSTEMED](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) à partir de NuGet. Ajoutez ensuite un appel à `UseSystemd` à la méthode `CreateHostBuilder` dans `Program.cs`.

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
> Si l’application n’est pas exécutée en tant que service Linux, la méthode `UseSystemd` ne fait rien.

À présent, publiez votre application (dépendante de l’infrastructure ou autonome pour le runtime Linux approprié, par exemple, `linux-x64`), à partir de Visual Studio en cliquant avec le bouton droit sur le projet et en sélectionnant *publier* dans le menu contextuel, ou à partir de la CLI .net core à l’aide de la commande suivante.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Copiez le contenu complet du répertoire `publish` dans un dossier d’installation sur l’hôte Linux. L’inscription du service nécessite l’ajout d’un fichier spécial, appelé « fichier d’unité », au répertoire `/etc/systemd/system`. Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier. Nommez le fichier avec l’identificateur que vous souhaitez `systemd` utiliser, ainsi que l’extension `.service`. Par exemple, `/etc/systemd/system/myapp.service`.

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

La propriété `Type=notify` indique `systemd` que l’application l’avertira au démarrage et à l’arrêt. Le paramètre `WantedBy=multi-user.target` entraîne le démarrage du service lorsque le système Linux atteint « runlevel 2 », ce qui signifie qu’un interpréteur de commandes multi-utilisateur non graphique est actif.

Avant que `systemd` ne reconnaisse le service, il doit recharger sa configuration. Vous pouvez contrôler `systemd` à l’aide de la commande `systemctl`. Après le rechargement, utilisez la sous-commande `status` pour confirmer que l’application s’est correctement inscrite.

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

Utilisez la commande `start` pour démarrer le service.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> L’extension de `.service` est facultative lors de l’utilisation de `systemctl start`.

Pour indiquer à `systemd` de démarrer le service automatiquement au démarrage du système, utilisez la commande `enable`.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Consigner dans le journal

L’équivalent Linux du journal des événements Windows est `journald`, un service de système de journalisation structuré qui fait partie de `systemd`. Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement écrits dans `journald`, afin de configurer les niveaux de journalisation, utilisez la section `Console` de la configuration de la journalisation. La méthode du générateur d’hôtes `UseSystemd` configure automatiquement le format de sortie de la console pour l’adapter au journal.

Étant donné que `journald` est la norme pour les journaux Linux, il existe un large éventail d’outils qui s’intègrent avec elle et vous pouvez facilement router les journaux d' `journald` vers un système de journalisation externe. Travailler localement sur l’hôte, vous pouvez utiliser la commande `journalctl` pour afficher les journaux à partir de la ligne de commande.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.

Pour en savoir plus sur l’interrogation du journal système à partir de la ligne de commande avec `journalctl`, consultez [les pages man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificats HTTPs pour les applications auto-hébergées

Lors de l’exécution d’une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée. Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.

Sur les hôtes Windows, le certificat peut être chargé à partir d’un [magasin de certificats](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la classe <xref:System.Security.Cryptography.X509Certificates.X509Store>. La classe `X509Store` peut également être utilisée avec le magasin de clés OpenSSL sur certains hôtes Linux.

Les certificats peuvent également être créés à l’aide de l’un des [constructeurs X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), soit à partir d’un fichier (par exemple, un fichier `.pfx` protégé par un mot de passe fort), soit à partir de données binaires récupérées à partir d’un service de stockage sécurisé tel que [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).

Kestrel peut être configuré pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.

### <a name="set-https-certificates-using-configuration"></a>Définir des certificats HTTPs à l’aide de la configuration

L’approche de configuration requiert la définition du chemin d’accès au fichier de `.pfx` de certificat et du mot de passe dans la section de configuration Kestrel. Dans `appsettings.json` qui ressemble à ceci.

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

Pour configurer HTTPs sur Kestrel dans le code, utilisez la méthode `ConfigureKestrel` sur `IWebHostBuilder` dans la classe `Program`.

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

Là encore, le mot de passe du fichier de `.pfx` doit être stocké dans et extrait d’une source de configuration sécurisée.

>[!div class="step-by-step"]
>[Précédent](grpc-in-production.md)
>[Suivant](docker.md)
