---
title: Fournisseurs de configuration dans .NET
description: Découvrez comment l’API du fournisseur de configuration est utilisée pour configurer des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: 036eb403318200bc0ae1d93e2c7cf9d074cb0bfb
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899446"
---
# <a name="configuration-providers-in-net"></a>Fournisseurs de configuration dans .NET

La configuration dans .NET est possible avec les fournisseurs de configuration. Il existe plusieurs types de fournisseurs qui reposent sur différentes sources de configuration. Cet article détaille tous les différents fournisseurs de configuration et leurs sources correspondantes.

- [Fournisseur de configuration de fichier](#file-configuration-provider)
- [Fournisseur de configuration de variable d’environnement](#environment-variable-configuration-provider)
- [Fournisseur de configuration de ligne de commande](#command-line-configuration-provider)
- [Fournisseur de configuration de clé par fichier](#key-per-file-configuration-provider)
- [Fournisseur de configuration de la mémoire](#memory-configuration-provider)

## <a name="file-configuration-provider"></a>Fournisseur de configuration de fichier

<xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> est la classe de base pour charger la configuration à partir du système de fichiers. Les fournisseurs de configuration suivants dérivent de `FileConfigurationProvider` :

- [Fournisseur de configuration JSON](#json-configuration-provider)
- [Fournisseur de configuration XML](#xml-configuration-provider)
- [Fournisseur de configuration INI](#ini-configuration-provider)

### <a name="json-configuration-provider"></a>Fournisseur de configuration JSON

La <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> classe charge la configuration à partir d’un fichier JSON. Installez le [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) package NuGet.

Les surcharges peuvent spécifier :

- Indique si le fichier est facultatif
- Si la configuration est rechargée en cas de modification du fichier

Considérez le code suivant :

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

Le code précédent :

- Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.
- Configure le fournisseur de configuration JSON pour charger le *appsettings.jssur* et  *appSettings*. `Environment` fichiers *JSON* avec les options suivantes :
  - `optional: true`: Le fichier est facultatif.
  - `reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.

Les paramètres JSON sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).

Voici un exemple *appsettings.jssur* un fichier avec différents paramètres de configuration :

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

À partir de l' <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, après avoir ajouté des fournisseurs de configuration, vous pouvez appeler <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> pour obtenir l' <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> objet. La racine de configuration représente la racine d’une hiérarchie de configuration. Les sections de la configuration peuvent être liées à des instances d’objets .NET, et fournies ultérieurement comme par le biais de l' <xref:Microsoft.Extensions.Options.IOptions%601> injection de dépendances.

Prenons le `TransientFaultHandlingOptions` type d’enregistrement défini comme suit :

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

Pour plus d’informations sur les types d’enregistrements, consultez [types d’enregistrements en C# 9](../../csharp/whats-new/csharp-9.md#record-types).

Le code suivant génère la racine de configuration, lie une section au `TransientFaultHandlingOptions` type d’enregistrement et imprime les valeurs liées dans la fenêtre de console :

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

L’application écrirait l’exemple de sortie suivant :

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a>Fournisseur de configuration XML

La <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> classe charge la configuration à partir d’un fichier XML au moment de l’exécution. Installez le [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) package NuGet.

Le code suivant illustre la configuration de fichiers XML à l’aide du fournisseur de configuration XML.

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

Le code précédent :

- Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.
- Configure le fournisseur de configuration XML pour charger les fichiers *appsettings.xml* et *repeating-example.xml* avec les options suivantes :
  - `optional: true`: Le fichier est facultatif.
  - `reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.
- Configure le fournisseur de configuration des variables d’environnement.
- Configure le fournisseur de configuration de ligne de commande si le donné `args` contient des arguments.

Les paramètres XML sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).

Voici un exemple *appsettings.xml* fichier avec différents paramètres de configuration :

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

Les éléments répétitifs qui utilisent le même nom d’élément fonctionnent si l’attribut `name` est utilisé pour distinguer les éléments :

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

Le code suivant lit le fichier de configuration précédent et affiche les clés et les valeurs :

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

L’application écrirait l’exemple de sortie suivant :

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

Les attributs peuvent être utilisés pour fournir des valeurs :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

Le fichier de configuration précédent charge les clés suivantes avec `value` :

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a>Fournisseur de configuration INI

La <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> classe charge la configuration à partir d’un fichier ini au moment de l’exécution. Installez le [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  package NuGet.

Le code suivant efface tous les fournisseurs de configuration et ajoute le `IniConfigurationProvider` avec deux fichiers ini comme source :

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

Voici un exemple *appsettings.ini* fichier avec différents paramètres de configuration :

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

Le code suivant affiche les paramètres de configuration précédents en les écrivant dans la fenêtre de console :

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

L’application écrirait l’exemple de sortie suivant :

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a>Fournisseur de configuration de variable d’environnement

À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> charge la configuration à partir des paires clé-valeur de variable d’environnement après la lecture *appsettings.jssur*, *appSettings.* `Environment` *. JSON* et le gestionnaire de secret. Par conséquent, les valeurs de clés lues à partir de l’environnement remplacent les valeurs lues à partir de *appsettings.jssur*, *appSettings.* `Environment` *. JSON* et le gestionnaire de secret.

Le `:` séparateur ne fonctionne pas avec les clés hiérarchiques de variable d’environnement sur toutes les plateformes. Le trait de soulignement double ( `__` ) est automatiquement remplacé par un `:` et est pris en charge par toutes les plateformes. Par exemple, le `:` séparateur n’est pas pris en charge par [bash](https://linuxhint.com/bash-environment-variables), mais `__` est.

Les `set` commandes suivantes :

- Définissez les clés et les valeurs d’environnement de l’exemple précédent sur Windows.
- Testez les paramètres en les remplaçant par leurs valeurs par défaut. La `dotnet run` commande doit être exécutée dans le répertoire du projet.

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

Paramètres d’environnement précédents :

- Sont uniquement définies dans les processus lancés à partir de la fenêtre de commande dans laquelle ils ont été définis.
- Ne seront pas lues par les applications Web lancées avec Visual Studio.

Les commandes [setx](/windows-server/administration/windows-commands/setx) suivantes peuvent être utilisées pour définir les clés et les valeurs d’environnement sur Windows. Contrairement à `set` , `setx` les paramètres sont conservés. `/M` définit la variable dans l’environnement système. Si le `/M` commutateur n’est pas utilisé, une variable d’environnement utilisateur est définie.

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

Pour vérifier que les commandes précédentes remplacent *appsettings.jssur* et *appSettings.* `Environment` *. JSON*:

- Avec Visual Studio : quittez et redémarrez Visual Studio.
- Avec l’interface CLI : démarrez une nouvelle fenêtre de commande et entrez `dotnet run` .

Appelez <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> avec une chaîne pour spécifier un préfixe pour les variables d’environnement :

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

Dans le code précédent :

- `config.AddEnvironmentVariables(prefix: "CustomPrefix_")` est ajouté après les fournisseurs de configuration par défaut. Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).
- Les variables d’environnement définies avec le `CustomPrefix_` préfixe remplacent les fournisseurs de configuration par défaut. Cela comprend les variables d’environnement sans le préfixe.

Le préfixe est supprimé lorsque les paires clé-valeur de configuration sont lues.

Les commandes suivantes testent le préfixe personnalisé :

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

La configuration par défaut charge les variables d’environnement et les arguments de ligne de commande précédés du préfixe `DOTNET_` . Le `DOTNET_` préfixe est utilisé par .net pour la [configuration](generic-host.md#app-configuration)de l' [hôte](generic-host.md#host-configuration) et de l’application, mais pas pour la configuration de l’utilisateur.

Pour plus d’informations sur la configuration de l’hôte et de l’application, consultez [hôte générique .net](generic-host.md).

Dans [Azure App service](https://azure.microsoft.com/services/app-service), sélectionnez **nouveau paramètre d’application** dans la page **paramètres > configuration** . Azure App Service paramètres de l’application sont les suivants :

- Chiffré au repos et transmis sur un canal chiffré.
- Exposés en tant que variables d’environnement.

### <a name="connection-string-prefixes"></a>Préfixes des chaînes de connexion

L’API de configuration a des règles de traitement spéciales pour quatre variables d’environnement de chaîne de connexion. Ces chaînes de connexion sont impliquées dans la configuration des chaînes de connexion Azure pour l’environnement de l’application. Les variables d’environnement avec les préfixes indiqués dans le tableau sont chargées dans l’application avec la configuration par défaut ou lorsqu’aucun préfixe n’est fourni à `AddEnvironmentVariables` .

| Préfixe de la chaîne de connexion | Fournisseur                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | Fournisseur personnalisé                                                         |
| `MYSQLCONNSTR_`          | [MySQL](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [Azure SQL Database](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [SQL Server](https://www.microsoft.com/sql-server)                      |

Quand une variable d’environnement est découverte et chargée dans la configuration avec l’un des quatre préfixes indiqués dans le tableau :

- La clé de configuration est créée en supprimant le préfixe de la variable d’environnement et en ajoutant une section de clé de configuration (`ConnectionStrings`).
- Une nouvelle paire clé-valeur de configuration est créée qui représente le fournisseur de connexion de base de données (à l’exception de `CUSTOMCONNSTR_`, qui ne possède aucun fournisseur indiqué).

| Clé de variable d’environnement | Clé de configuration convertie | Entrée de configuration de fournisseur                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | Entrée de configuration non créée.                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | Clé : `ConnectionStrings:{KEY}_ProviderName` :<br>Valeur: `MySql.Data.MySqlClient` |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | Clé : `ConnectionStrings:{KEY}_ProviderName` :<br>Valeur: `System.Data.SqlClient`  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | Clé : `ConnectionStrings:{KEY}_ProviderName` :<br>Valeur: `System.Data.SqlClient`  |

### <a name="environment-variables-set-in-launchsettingsjson"></a>Variables d’environnement définies dans launchSettings.jssur

Les variables d’environnement définies dans *launchSettings.jslors de* la substitution de celles définies dans l’environnement système.

## <a name="command-line-configuration-provider"></a>Fournisseur de configuration de ligne de commande

À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> charge la configuration à partir de paires clé-valeur d’argument de ligne de commande après les sources de configuration suivantes :

- *appsettings.jssur* et *appSettings*. `Environment` fichiers *JSON* .
- Secrets d’application (gestionnaire de secret) dans l' `Development` environnement.
- Variables d'environnement.

Par défaut, les valeurs de configuration définies sur la ligne de commande remplacent les valeurs de configuration définies avec tous les autres fournisseurs de configuration.

### <a name="command-line-arguments"></a>Arguments de ligne de commande

La commande suivante définit des clés et des valeurs à l’aide de `=` :

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

La commande suivante définit des clés et des valeurs à l’aide de `/` :

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

La commande suivante définit des clés et des valeurs à l’aide de `--` :

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

Valeur de la clé :

- Doit suivre `=` ou la clé doit avoir un préfixe `--` ou `/` lorsque la valeur suit un espace.
- N’est pas obligatoire si `=` est utilisé. Par exemple : `SomeKey=`.

Dans la même commande, ne mélangez pas les paires clé-valeur d’argument de ligne de commande qui utilisent `=` des paires clé-valeur utilisant un espace.

## <a name="key-per-file-configuration-provider"></a>Fournisseur de configuration de clé par fichier

Le <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> utilise les fichiers d’un répertoire en tant que paires clé-valeur de configuration. La clé est le nom de fichier. La valeur est le contenu du fichier. Le fournisseur de configuration par fichier clé est utilisé dans les scénarios d’hébergement de l’ancrage.

Pour activer la configuration clé par fichier, appelez la méthode d’extension <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> sur une instance de <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>. Le `directoryPath` aux fichiers doit être un chemin d’accès absolu.

Les surcharges permettent de spécifier :

- Un délégué `Action<KeyPerFileConfigurationSource>` qui configure la source.
- Si le répertoire est facultatif et le chemin d’accès au répertoire.

Le double trait de soulignement (`__`) est utilisé comme un délimiteur de clé de configuration dans les noms de fichiers. Par exemple, le nom de fichier `Logging__LogLevel__System` génère la clé de configuration `Logging:LogLevel:System`.

Appelez `ConfigureAppConfiguration` lors de la création de l’hôte pour spécifier la configuration de l’application :

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a>Fournisseur de configuration de la mémoire

Le <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> utilise une collection en mémoire en tant que paires clé-valeur de configuration.

Le code suivant ajoute une collection de mémoire au système de configuration :

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

Dans le code précédent, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> ajoute le fournisseur de mémoire après les fournisseurs de configuration par défaut. Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).

## <a name="see-also"></a>Voir aussi

- [Configuration dans .NET](configuration.md)
- [Hôte générique .NET](generic-host.md)
- [Implémenter un fournisseur de configuration personnalisé](custom-configuration-provider.md)
