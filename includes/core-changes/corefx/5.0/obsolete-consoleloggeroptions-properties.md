---
ms.openlocfilehash: e92fe8364800b1775f0acc31d67aef66a42d0b95
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465882"
---
### <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="e0a81-101">Propriétés obsolètes sur ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="e0a81-101">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="e0a81-102">Le <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type et certaines propriétés sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e0a81-102">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e0a81-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e0a81-103">Change description</span></span>

<span data-ttu-id="e0a81-104">À compter de .NET 5,0, le <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type et plusieurs propriétés sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e0a81-104">Starting in .NET 5.0, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="e0a81-105">Les propriétés obsolètes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0a81-105">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="e0a81-106">Avec l’introduction de nouveaux formateurs, ces propriétés sont désormais disponibles sur les formateurs individuels.</span><span class="sxs-lookup"><span data-stu-id="e0a81-106">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e0a81-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e0a81-107">Reason for change</span></span>

<span data-ttu-id="e0a81-108">La <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> propriété est un type énumération, qui ne peut pas représenter un formateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e0a81-108">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="e0a81-109">Les propriétés restantes ont été définies sur <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> et appliquées aux deux formats intégrés pour les journaux de la console.</span><span class="sxs-lookup"><span data-stu-id="e0a81-109">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="e0a81-110">Toutefois, avec l’introduction d’une nouvelle API Formatter, il est plus judicieux de faire en sorte que la mise en forme soit représentée sur les options spécifiques au formateur.</span><span class="sxs-lookup"><span data-stu-id="e0a81-110">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="e0a81-111">Cette modification offre une meilleure séparation entre l’enregistreur d’événements et les formateurs d’enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="e0a81-111">This change provides better separation between the logger and logger formatters.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e0a81-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e0a81-112">Version introduced</span></span>

<span data-ttu-id="e0a81-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e0a81-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e0a81-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e0a81-114">Recommended action</span></span>

- <span data-ttu-id="e0a81-115">Utilisez la nouvelle <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> propriété à la place de la <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="e0a81-115">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e0a81-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0a81-116">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="e0a81-117">Il existe plusieurs différences entre <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> et <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> :</span><span class="sxs-lookup"><span data-stu-id="e0a81-117">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="e0a81-118"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> n’a que deux options possibles : `Default` et `Systemd` .</span><span class="sxs-lookup"><span data-stu-id="e0a81-118"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="e0a81-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> ne respecte pas la casse et peut être n’importe quelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0a81-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="e0a81-120">Les noms intégrés réservés sont `Simple` , `Systemd` et `Json` (.net 5,0 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="e0a81-120">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5.0 and later).</span></span>
  - <span data-ttu-id="e0a81-121">`"Format": "Systemd"` correspond à `"FormatterName": "Systemd"`.</span><span class="sxs-lookup"><span data-stu-id="e0a81-121">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="e0a81-122">`"Format": "Default"` correspond à `"FormatterName": "Simple"`.</span><span class="sxs-lookup"><span data-stu-id="e0a81-122">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="e0a81-123">Pour les <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> Propriétés,, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> et <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> , utilisez à la place la propriété correspondante sur les nouveaux <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> types, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> ou <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> .</span><span class="sxs-lookup"><span data-stu-id="e0a81-123">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="e0a81-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0a81-124">For example:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

<span data-ttu-id="e0a81-125">Les deux extraits de code JSON suivants montrent comment le fichier de configuration change.</span><span class="sxs-lookup"><span data-stu-id="e0a81-125">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="e0a81-126">Ancien fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="e0a81-126">Old configuration file:</span></span>

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

<span data-ttu-id="e0a81-127">Nouveau fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="e0a81-127">New configuration file:</span></span>

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

#### <a name="category"></a><span data-ttu-id="e0a81-128">Category</span><span class="sxs-lookup"><span data-stu-id="e0a81-128">Category</span></span>

- <span data-ttu-id="e0a81-129">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0a81-129">Core .NET libraries</span></span>
- <span data-ttu-id="e0a81-130">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e0a81-130">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0a81-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="e0a81-131">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
