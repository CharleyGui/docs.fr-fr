---
title: Applications gRPC auto-hébergées-gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC sous forme de services auto-hébergés.
ms.date: 09/02/2019
ms.openlocfilehash: 2244f161ad4b5d60138ae0f7b4d6a9c8c8829aa8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503402"
---
# <a name="self-hosted-grpc-applications"></a>Applications gRPC auto-hébergées

Bien que les applications ASP.NET Core 3,0 puissent être hébergées dans IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS, car certaines des fonctionnalités HTTP/2 ne sont pas prises en charge. Cette fonctionnalité est un objectif pour une future mise à jour de Windows Server.

Vous pouvez exécuter votre application en tant que service Windows. Vous pouvez aussi l’exécuter en tant que service Linux contrôlé par [SystemD](https://en.wikipedia.org/wiki/Systemd), en raison des nouvelles fonctionnalités des extensions d’hébergement .net Core 3,0.

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

À présent, publiez votre application à l’aide de l’une des méthodes suivantes :

* Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel.
* À partir de la CLI .NET Core.

Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du Framework* ou un déploiement *autonome* . Les déploiements dépendants du Framework requièrent l’installation du runtime partagé .NET Core sur l’hôte sur lequel ils sont exécutés. Les déploiements autonomes sont publiés avec une copie complète du runtime et du Framework .NET Core et peuvent être exécutés sur n’importe quel hôte. Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, consultez la documentation sur le [déploiement d’applications .net Core](../../core/deploying/index.md) .

Pour publier une version autonome de l’application qui ne nécessite pas l’installation du Runtime .NET Core 3,0 sur l’ordinateur hôte, spécifiez le runtime à inclure dans l’application. Utilisez l’indicateur `-r` (ou `--runtime`).

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Pour publier une build dépendante de l’infrastructure, omettez l’indicateur `-r`.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Copiez le contenu complet du répertoire `publish` dans un dossier d’installation. Utilisez ensuite l' [outil SC](/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour le fichier exécutable.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Consigner dans le journal des événements Windows

La méthode `UseWindowsService` ajoute automatiquement un fournisseur de [journalisation](/aspnet/core/fundamentals/logging/) qui écrit des messages de journal dans le journal des événements Windows. Vous pouvez configurer la journalisation pour ce fournisseur en ajoutant une entrée `EventLog` à la section `Logging` de `appsettings.json` ou une autre source de configuration. 

Vous pouvez remplacer le nom de la source utilisé dans le journal des événements en définissant une propriété de `SourceName` dans ces paramètres. Si vous ne spécifiez pas de nom, le nom de l’application par défaut (normalement, le nom de l’assembly exécutable) sera utilisé.

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

À présent, publiez votre application. L’application peut être soit dépendante de l’infrastructure, soit autonome pour le runtime Linux concerné (par exemple, `linux-x64`). Vous pouvez publier à l’aide de l’une des méthodes suivantes :

* Dans Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **publier** dans le menu contextuel. 
* À partir de la CLI .NET Core, à l’aide de la commande suivante :

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
Copiez le contenu complet du répertoire `publish` dans un dossier d’installation sur l’hôte Linux. L’inscription du service nécessite l’ajout d’un fichier spécial, appelé *fichier d’unité*, au répertoire `/etc/systemd/system`. Vous aurez besoin de l’autorisation racine pour créer un fichier dans ce dossier. Nommez le fichier avec l’identificateur que vous souhaitez `systemd` utiliser, ainsi que l’extension `.service`. Par exemple, utilisez `/etc/systemd/system/myapp.service`.

Le fichier de service utilise le format INI, comme le montre l’exemple suivant :

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

Avant que `systemd` ne reconnaisse le service, il doit recharger sa configuration. Vous pouvez contrôler `systemd` à l’aide de la commande `systemctl`. Après le rechargement, utilisez la sous-commande `status` pour vérifier que l’application s’est correctement inscrite.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Si vous avez correctement configuré le service, vous obtiendrez la sortie suivante :

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
> L’extension de `.service` est facultative lorsque vous utilisez `systemctl start`.

Pour indiquer à `systemd` de démarrer le service automatiquement au démarrage du système, utilisez la commande `enable`.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Consigner dans le journal

L’équivalent Linux du journal des événements Windows est `journald`, un service de système de journalisation structuré qui fait partie de `systemd`. Les messages de journal écrits dans la sortie standard par un démon Linux sont automatiquement écrits dans `journald`. Pour configurer les niveaux de journalisation, utilisez la section `Console` de la configuration de la journalisation. La méthode du générateur d’hôtes `UseSystemd` configure automatiquement le format de sortie de la console pour l’adapter au journal.

Étant donné que `journald` est la norme pour les journaux Linux, un large éventail d’outils s’y intègre. Vous pouvez facilement acheminer les journaux de `journald` vers un système de journalisation externe. Travailler localement sur l’hôte, vous pouvez utiliser la commande `journalctl` pour afficher les journaux à partir de la ligne de commande.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Si un environnement d’interface utilisateur graphique est disponible sur votre ordinateur hôte, quelques visionneuses de journaux graphiques sont disponibles pour Linux, telles que *QJournalctl* et *gnome-logs*.

Pour en savoir plus sur l’interrogation du journal `systemd` à partir de la ligne de commande à l’aide de `journalctl`, consultez [les pages man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificats HTTPs pour les applications auto-hébergées

Lorsque vous exécutez une application gRPC en production, vous devez utiliser un certificat TLS provenant d’une autorité de certification approuvée. Il peut s’agir d’une autorité de certification publique ou d’une autorité de certification interne pour votre organisation.

Sur les hôtes Windows, vous pouvez charger le certificat à partir d’un [magasin de certificats](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé à l’aide de la classe <xref:System.Security.Cryptography.X509Certificates.X509Store>. Vous pouvez également utiliser la classe `X509Store` avec le magasin de clés OpenSSL sur certains hôtes Linux.

Vous pouvez également créer des certificats à l’aide de l’un des [constructeurs X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), à partir des éléments suivants :

* Un fichier, tel qu’un fichier `.pfx` protégé par un mot de passe fort
* Données binaires récupérées à partir d’un service de stockage sécurisé, par exemple [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Vous pouvez configurer Kestrel pour utiliser un certificat de deux manières : à partir de la configuration ou dans le code.

### <a name="set-https-certificates-by-using-configuration"></a>Définir des certificats HTTPs à l’aide de la configuration

L’approche de configuration requiert la définition du chemin d’accès au fichier de `.pfx` de certificat et du mot de passe dans la section de configuration Kestrel. Dans `appsettings.json`, cela ressemble à ceci :

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

Fournissez le mot de passe à l’aide d’une source de configuration sécurisée telle que Azure Key Vault ou le coffre Hashicorp.

> [!IMPORTANT]
> Ne stockez pas les mots de passe non chiffrés dans les fichiers de configuration.

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

Là encore, veillez à stocker le mot de passe pour le fichier `.pfx` dans et à le récupérer à partir d’une source de configuration sécurisée.

>[!div class="step-by-step"]
>[Précédent](grpc-in-production.md)
>[Suivant](docker.md)
