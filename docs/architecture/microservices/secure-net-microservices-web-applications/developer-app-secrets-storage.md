---
title: Stockage sécurisé des secrets d’application en phase de développement
description: Sécurité dans les microservices .NET et les applications web - Ne stockez pas vos secrets d’application, tels que mots de passe, chaînes de connexion ou clés API, dans le contrôle de code source. Découvrez les options que vous pouvez utiliser dans ASP.NET Core, en particulier comment gérer les « secrets utilisateur ».
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501800"
---
# <a name="store-application-secrets-safely-during-development"></a>Stocker des secrets d’application en toute sécurité pendant le développement

Pour se connecter à des ressources protégées et à d’autres services, les applications ASP.NET Core doivent généralement utiliser des chaînes de connexion, des mots de passe ou d’autres informations d’identification qui contiennent des informations sensibles. Ces informations sensibles sont appelées *secrets*. La bonne pratique consiste à ne pas inclure les secrets dans le code source, et à veiller à ne pas les stocker dans le contrôle de code source. Au lieu de cela, vous devez utiliser le modèle de configuration ASP.NET Core pour lire les secrets à partir d’emplacements plus sécurisés.

Vous devez distinguer les secrets destinés à accéder aux ressources de développement et de préproduction de ceux utilisés pour accéder aux ressources de production, car ce ne sont pas les mêmes personnes qui ont besoin d’accéder à ces différents jeux de secrets. Dans la pratique, les secrets utilisés en phase de développement sont généralement stockés dans des variables d’environnement ou avec l’outil Secret Manager d’ASP.NET Core. Pour un stockage plus sécurisé dans les environnements de production, les microservices peuvent stocker les secrets dans Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Stocker des secrets dans des variables d’environnement

Pour les développeurs, l’un des moyens de maintenir les secrets en dehors du code source est de définir des secrets basés sur des chaînes prenant la forme de [variables d’environnement](/aspnet/core/security/app-secrets#environment-variables) sur leurs machines de développement. Quand vous utilisez des variables d’environnement pour stocker des secrets avec des noms hiérarchisés (tels que ceux imbriqués dans des sections de configuration), vous devez nommer les variables de façon à inclure la hiérarchie complète de leurs sections, en les séparant de deux-points (:).

Par exemple, le fait d’affecter la valeur `Logging:LogLevel:Default` à une variable d’environnement `Debug` équivaudrait à une valeur de configuration du fichier JSON suivant :

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Pour accéder à ces valeurs de variables d’environnement, l’application doit simplement appeler AddEnvironmentVariables sur son ConfigurationBuilder pendant la construction d’un objet IConfigurationRoot.

Notez que les variables d’environnement sont couramment stockées en texte clair. Par conséquent, si la machine ou le processus comprenant les variables d’environnement est compromis, les valeurs des variables d’environnement sont visibles.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Stocker des secrets à l’aide de l’outil Secret Manager d’ASP.NET Core

L’outil ASP.NET Core [secret Manager](/aspnet/core/security/app-secrets#secret-manager) fournit une autre méthode pour conserver les secrets en dehors du code source **pendant le développement**. Pour utiliser l’outil Secret Manager, installez le package **Microsoft.Extensions.Configuration.SecretManager** dans votre fichier projet. Une fois cette dépendance présente et restaurée, vous pouvez utiliser la commande `dotnet user-secrets` pour définir la valeur des secrets à partir de la ligne de commande. Ces secrets sont alors stockés dans un fichier JSON dans le répertoire du profil de l’utilisateur (les détails varient selon le système d’exploitation), à l’écart du code source.

Les secrets définis par l’outil Secret Manager sont organisés par la propriété `UserSecretsId` du projet qui utilise les secrets. Par conséquent, veillez à définir la propriété UserSecretsId dans votre fichier projet, comme indiqué dans l’extrait de code ci-dessous. La valeur par défaut est un GUID assigné par Visual Studio, mais la chaîne réelle n’a pas d’importance tant qu’elle est unique sur votre ordinateur.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Pour utiliser les secrets stockés avec Secret Manager dans une application, `AddUserSecrets<T>` est appelé au niveau de l’instance ConfigurationBuilder. Les secrets de l’application sont alors inclus dans sa configuration. Le paramètre générique T doit être un type de l’assembly auquel UserSecretId a été appliqué. Généralement, l’utilisation de `AddUserSecrets<Startup>` convient.

`AddUserSecrets<Startup>()` est inclus dans les options par défaut pour l’environnement de développement lors de l’utilisation de la méthode `CreateDefaultBuilder` dans *Program.cs*.

>[!div class="step-by-step"]
>[Précédent](authorization-net-microservices-web-applications.md)
>[Suivant](azure-key-vault-protects-secrets.md)
