---
title: Configuration dans .NET
description: Découvrez comment utiliser l’API de configuration de pour configurer des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: f97bd3fd4881c6b0939635ec2372aee21c670d5d
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720812"
---
# <a name="configuration-in-net"></a>Configuration dans .NET

La configuration dans .NET est effectuée à l’aide d’un ou de plusieurs [fournisseurs de configuration](#configuration-providers). Les fournisseurs de configuration lisent les données de configuration des paires clé-valeur à l’aide d’une variété de sources de configuration :

- Fichiers de paramètres, tels que *appsettings.jssur*
- Variables d'environnement
- [Azure Key Vault](/azure/key-vault/general/overview)
- [Azure App Configuration](/azure/azure-app-configuration/overview)
- Arguments de ligne de commande
- Fournisseurs personnalisés, installés ou créés
- Fichiers de répertoire
- Objets .NET en mémoire

## <a name="configure-console-apps"></a>Configurer des applications console

Les nouvelles applications de console .NET créées à l’aide de [dotnet New](../tools/dotnet-new.md) ou de Visual Studio n’exposent *pas* de fonctionnalités de configuration. Pour ajouter une configuration dans une nouvelle application de console .NET, [Ajoutez une référence de package](../tools/dotnet-add-package.md) à `Microsoft.Extensions.Hosting` . Modifiez le fichier *Program.cs* de façon à ce qu’il corresponde au code suivant :

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

La <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> méthode fournit la configuration par défaut pour l’application dans l’ordre suivant :

1. [ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) : ajoute un existant `IConfiguration` en tant que source.
1. *appsettings.jssur* l’utilisation du [fournisseur de configuration JSON](configuration-providers.md#file-configuration-provider).
1. *appSettings.* `Environment` *. JSON* à l’aide du [fournisseur de configuration JSON](configuration-providers.md#file-configuration-provider). Par exemple, *appSettings*. ***Production***. *JSON* et *appSettings*. ***Développement***. *JSON*.
1. Secrets d’application lorsque l’application s’exécute dans l' `Development` environnement.
1. Variables d’environnement à l’aide du [fournisseur de configuration des variables d’environnement](configuration-providers.md#environment-variable-configuration-provider).
1. Arguments de ligne de commande à l’aide du [fournisseur de configuration de ligne de commande](configuration-providers.md#command-line-configuration-provider).

Les fournisseurs de configuration ajoutés ultérieurement remplacent les paramètres de clé précédents. Par exemple, si `SomeKey` est défini dans *appsettings.jssur* et dans l’environnement, la valeur d’environnement est utilisée. À l’aide des fournisseurs de configuration par défaut, le [fournisseur de configuration de ligne de commande](configuration-providers.md#command-line-configuration-provider) remplace tous les autres fournisseurs.

### <a name="binding"></a>Liaison

L’un des principaux avantages de la configuration dans .NET est la possibilité de lier des valeurs de configuration à des instances d’objets .NET. Par exemple, le fournisseur de configuration JSON peut être utilisé pour mapper * desappsettings.jssur des* fichiers à des objets .net et est utilisé avec l’injection de dépendances. Cela active le modèle d’options, le modèle d’options utilise des classes pour fournir un accès fortement typé aux groupes de paramètres associés.

## <a name="configuration-providers"></a>Fournisseurs de configuration

Le tableau suivant présente les fournisseurs de configuration disponibles pour les applications .NET Core.

| Fournisseur                                                                                                               | Fournit la configuration à partir de        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [Fournisseur de configuration Azure App](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | Azure App Configuration            |
| [Fournisseur de configuration Azure Key Vault](/azure/key-vault/general/tutorial-net-virtual-machine)                        | Azure Key Vault                    |
| [Fournisseur de configuration de ligne de commande](configuration-providers.md#command-line-configuration-provider)                  | Paramètres de ligne de commande            |
| [Fournisseur de configuration personnalisé](custom-configuration-provider.md)                                                      | Source personnalisée                      |
| [Fournisseur de configuration des variables d’environnement](configuration-providers.md#environment-variable-configuration-provider) | Variables d'environnement              |
| [Fournisseur de configuration de fichier](configuration-providers.md#file-configuration-provider)                                  | Fichiers JSON, XML et INI           |
| [Fournisseur de configuration de clé par fichier](configuration-providers.md#key-per-file-configuration-provider)                  | Fichiers de répertoire                    |
| [Fournisseur de configuration de la mémoire](configuration-providers.md#memory-configuration-provider)                              | Collections en mémoire              |
| [Secrets d’application (gestionnaire de secret)](/aspnet/core/security/app-secrets)                                                      | Fichier dans le répertoire de profil utilisateur |

Pour plus d’informations sur les différents fournisseurs de configuration, consultez [fournisseurs de configuration dans .net](configuration-providers.md).

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de configuration dans .NET](configuration-providers.md)
- [Implémenter un fournisseur de configuration personnalisé](custom-configuration-provider.md)
