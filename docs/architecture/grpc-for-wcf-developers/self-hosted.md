---
title: Applications gRPC auto-hébergées - gRPC pour les développeurs WCF
description: Déploiement d’applications ASP.NET Core gRPC en tant que services auto-hébergés.
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147800"
---
# <a name="self-hosted-grpc-applications"></a>Applications gRPC auto-hébergées

Bien que ASP.NET applications Core 3.0 puissent être hébergées dans l’IIS sur Windows Server, il n’est actuellement pas possible d’héberger une application gRPC dans IIS parce qu’une partie de la fonctionnalité HTTP/2 n’est pas prise en charge. Cette fonctionnalité est un objectif pour une future mise à jour de Windows Server.

Vous pouvez exécuter votre application en tant que service Windows. Ou vous pouvez l’exécuter comme un service Linux contrôlé par [système](https://en.wikipedia.org/wiki/Systemd), en raison de nouvelles fonctionnalités dans les extensions d’hébergement .NET Core 3.0.

## <a name="run-your-app-as-a-windows-service"></a>Exécutez votre application comme un service Windows

Pour configurer votre application ASP.NET Core pour fonctionner sous forme de service Windows, installez le forfait [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) à partir de NuGet. Ensuite, ajoutez `UseWindowsService` un `CreateHostBuilder` appel `Program.cs`à la méthode en .

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
> Si l’application n’est pas en `UseWindowsService` cours d’exécution comme un service Windows, la méthode ne fait rien.

Publiez maintenant votre application en utilisant l’une de ces méthodes :

* De Visual Studio en cliquant à droite sur le projet et en sélectionnant **Publiez** sur le menu raccourci.
* De la CLI .NET Core.

Lorsque vous publiez une application .NET Core, vous pouvez choisir de créer un déploiement *dépendant du cadre* ou un déploiement *autonome.* Les déploiements dépendants du cadre exigent que le temps de course partagé de base .NET soit installé sur l’hôte où ils sont exécutés. Les déploiements autonomes sont publiés avec une copie complète du temps d’exécution et du cadre .NET Core et peuvent être exécutés sur n’importe quel hôte. Pour plus d’informations, y compris les avantages et les inconvénients de chaque approche, consultez la documentation [de déploiement d’applications .NET Core.](../../core/deploying/index.md)

Pour publier une version autonome de l’application qui ne nécessite pas l’installation de l’heure d’exécution .NET Core 3.0 sur l’hôte, spécifiez l’heure d’exécution à inclure dans l’application. Utilisez `-r` le `--runtime`(ou) drapeau.

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Pour publier une construction dépendante du `-r` cadre, omettre le drapeau.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Copiez le contenu `publish` complet de l’annuaire à un dossier d’installation. Ensuite, utilisez [l’outil sc](/windows/desktop/services/controlling-a-service-using-sc) pour créer un service Windows pour le fichier exécutable.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Connectez-vous au journal de l’événement Windows

La `UseWindowsService` méthode ajoute automatiquement un fournisseur [de connexion](/aspnet/core/fundamentals/logging/) qui écrit des messages journalaux au journal de l’événement Windows. Vous pouvez configurer la connexion `EventLog` pour ce `Logging` fournisseur `appsettings.json` en ajoutant une entrée à la section ou à une autre source de configuration.

Vous pouvez remplacer le nom source utilisé dans `SourceName` le journal de l’événement en définissant une propriété dans ces paramètres. Si vous ne spécifiez pas un nom, le nom de l’application par défaut (normalement le nom d’assemblage exécutable) sera utilisé.

Plus d’informations sur l’enregistrement est à la fin de ce chapitre.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Exécutez votre application comme un service Linux avec

Pour configurer votre application ASP.NET Core pour fonctionner comme un service Linux (ou *daemon* dans le langage Linux), installez le paquet [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) de NuGet. Ensuite, ajoutez `UseSystemd` un `CreateHostBuilder` appel `Program.cs`à la méthode en .

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
> Si l’application n’est pas en `UseSystemd` cours d’exécution comme un service Linux, la méthode ne fait rien.

Publiez maintenant votre demande. L’application peut être dépendante du cadre ou autonome pour l’exécution Linux pertinente (par exemple, `linux-x64`). Vous pouvez publier en utilisant l’une de ces méthodes :

* De Visual Studio en cliquant à droite sur le projet et en sélectionnant **Publiez** sur le menu raccourci.
* De l’ERC de base .NET, en utilisant la commande suivante :

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Copiez le contenu `publish` complet de l’annuaire à un dossier d’installation sur l’hôte Linux. L’enregistrement du service nécessite un fichier spécial, appelé `/etc/systemd/system` *fichier unitaire,* à ajouter à l’annuaire. Vous aurez besoin d’une autorisation de racine pour créer un fichier dans ce dossier. Nommez le fichier avec `systemd` l’identifiant `.service` que vous souhaitez utiliser et l’extension. Par exemple, utilisez `/etc/systemd/system/myapp.service`.

Le fichier de service utilise le format INI, comme le montre cet exemple :

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

La `Type=notify` propriété `systemd` indique que l’application l’avisera sur le démarrage et l’arrêt. Le `WantedBy=multi-user.target` paramètre entraînera le démarrage du service lorsque le système Linux atteint le « niveau 2 », ce qui signifie qu’une coque multi-utilisateurs non graphique est active.

Avant `systemd` de reconnaître le service, il doit recharger sa configuration. Vous `systemd` contrôlez `systemctl` en utilisant la commande. Après le rechargement, `status` utilisez le sous-service pour confirmer que l’application s’est enregistrée avec succès.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Si vous avez configuré correctement le service, vous obtiendrez la sortie suivante :

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Utilisez `start` la commande pour démarrer le service.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> L’extension `.service` est facultative `systemctl start`lorsque vous utilisez .

Pour `systemd` vous dire de démarrer automatiquement le `enable` service sur le démarrage du système, utilisez la commande.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Log à journald

L’équivalent Linux du journal `journald`d’événements Windows est , un `systemd`service structuré de système de journalisation qui fait partie de . Les messages journal écrits à la sortie standard `journald`par un daemon Linux sont automatiquement écrits à . Pour configurer les niveaux `Console` d’enregistrement, utilisez la section de la configuration d’enregistrement. La `UseSystemd` méthode du constructeur d’hôtes configure automatiquement le format de sortie de la console pour convenir au journal.

Parce `journald` que c’est la norme pour les journaux Linux, une variété d’outils s’y intègrent. Vous pouvez facilement acheminer les journaux d’un `journald` système d’enregistrement externe. Travaillant localement sur l’hôte, `journalctl` vous pouvez utiliser la commande pour afficher les journaux depuis la ligne de commande.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Si vous disposez d’un environnement GUI disponible sur votre hôte, quelques internautes graphiques sont disponibles pour Linux, tels que *QJournalctl* et *gnome-logs*.

Pour en savoir plus `systemd` sur la requête du `journalctl`journal à partir de la ligne de commande en utilisant , voir [les pages de l’homme](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificats HTTPS pour les demandes auto-hébergées

Lorsque vous exécutez une demande de gRPC en production, vous devez utiliser un certificat TLS d’une autorité de certificat de confiance (CA). Ce CA peut être un CA public, ou un CA interne pour votre organisation.

Sur les hôtes Windows, vous pouvez charger le <xref:System.Security.Cryptography.X509Certificates.X509Store> certificat à partir d’un magasin de [certificat](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) sécurisé en utilisant la classe. Vous pouvez également `X509Store` utiliser la classe avec le magasin de clés OpenSSL sur certains hôtes Linux.

Vous pouvez également créer des certificats en utilisant l’un des [constructeurs X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), à partir de l’un ou l’autre:

* Un fichier, tel `.pfx` qu’un fichier protégé par un mot de passe fort
* Données binaires récupérées à partir d’un service de stockage sécurisé tel [qu’Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Vous pouvez configurer Kestrel pour utiliser un certificat de deux façons : de configuration ou de code.

### <a name="set-https-certificates-by-using-configuration"></a>Définissez les certificats HTTPS en utilisant la configuration

L’approche de configuration nécessite `.pfx` de définir le chemin vers le fichier de certificat et le mot de passe dans la section configuration Kestrel. En `appsettings.json`, qui ressemblerait à ceci:

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

Fournissez le mot de passe en utilisant une source de configuration sécurisée comme Azure Key Vault ou Hashicorp Vault.

> [!IMPORTANT]
> Ne stockez pas de mots de passe non chiffrés dans les fichiers de configuration.

### <a name="set-https-certificates-in-code"></a>Définissez les certificats HTTPS dans le code

Pour configurer HTTPS sur Kestrel `ConfigureKestrel` dans `IWebHostBuilder` le `Program` code, utilisez la méthode dans la classe.

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

Encore une fois, assurez-vous `.pfx` de stocker le mot de passe pour le fichier et le récupérer à partir d’une source de configuration sécurisée.

>[!div class="step-by-step"]
>[Suivant précédent](grpc-in-production.md)
>[Next](docker.md)
