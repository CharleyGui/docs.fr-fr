---
title: 'Modification avec rupture : propriétés obsolètes sur ConsoleLoggerOptions'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où le type ConsoleLoggerFormat et certaines propriétés sur ConsoleLoggerOptions sont désormais obsolètes.
ms.date: 11/01/2020
ms.openlocfilehash: bd039dfa84ae3399d7fb36f992010a9a3c9f6ddf
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548381"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a>Propriétés obsolètes sur ConsoleLoggerOptions

Le <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type et certaines propriétés sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> sont désormais obsolètes.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type et plusieurs propriétés sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> sont obsolètes. Les propriétés obsolètes sont les suivantes :

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

Avec l’introduction de nouveaux formateurs, ces propriétés sont désormais disponibles sur les formateurs individuels.

## <a name="reason-for-change"></a>Motif de modification

La <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> propriété est un type énumération, qui ne peut pas représenter un formateur personnalisé.

Les propriétés restantes ont été définies sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> et appliquées aux deux formats intégrés pour les journaux de la console. Toutefois, avec l’introduction d’une nouvelle API Formatter, il est plus judicieux de faire en sorte que la mise en forme soit représentée sur les options spécifiques au formateur. Cette modification offre une meilleure séparation entre l’enregistreur d’événements et les formateurs d’enregistreur d’événements.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Utilisez la nouvelle <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> propriété à la place de la <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> propriété. Par exemple :

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  Il existe plusieurs différences entre <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> et <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> :

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> n’a que deux options possibles : `Default` et `Systemd` .
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> ne respecte pas la casse et peut être n’importe quelle chaîne. Les noms intégrés réservés sont `Simple` , `Systemd` et `Json` (.net 5,0 et versions ultérieures).
  - `"Format": "Systemd"` correspond à `"FormatterName": "Systemd"`.
  - `"Format": "Default"` correspond à `"FormatterName": "Simple"`.

- Pour les <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> Propriétés,, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> et <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> , utilisez à la place la propriété correspondante sur les nouveaux <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> types, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> ou <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> . Par exemple, le paramètre correspondant pour <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> est <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> .

  Code précédent :

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  Nouveau code :

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

Les deux extraits de code JSON suivants montrent comment le fichier de configuration change. Ancien fichier de configuration :

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

Nouveau fichier de configuration :

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

## <a name="affected-apis"></a>API affectées

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
