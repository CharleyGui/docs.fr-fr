---
title: Mise en forme des journaux de la console
description: Découvrez comment utiliser la mise en forme de journal de la console disponible ou implémenter une mise en forme de journal personnalisée pour vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700818"
---
# <a name="console-log-formatting"></a>Mise en forme des journaux de la console

Dans .NET 5, la prise en charge de la mise en forme personnalisée a été ajoutée aux journaux de la console dans l' `Microsoft.Extensions.Logging.Console` espace de noms. Trois options de mise en forme prédéfinies sont disponibles : [`Simple`](#simple) , [`Systemd`](#systemd) et [`Json`](#json) .

> [!IMPORTANT]
> Auparavant, l' <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> énumération permettait de sélectionner le format de journal souhaité, lisible par l’utilisateur, qui était le `Default` ou une seule ligne, également appelée `Systemd` . Toutefois, ceux-ci n’étaient **pas** personnalisables et sont désormais dépréciés.

Dans cet article, vous allez découvrir les formateurs de journaux de console. L’exemple de code source montre comment :

- Inscrire un nouveau formateur
- Sélectionner un formateur inscrit à utiliser
  - Par le biais du code ou de la [configuration](configuration.md)
- Implémenter un formateur personnalisé
  - Mettre à jour la configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>
  - Activer la mise en forme personnalisée des couleurs

## <a name="register-formatter"></a>Inscrire le formateur

Le module [ `Console` fournisseur de journalisation](logging-providers.md#console) comporte plusieurs formateurs prédéfinis et expose la possibilité de créer votre propre formateur personnalisé. Pour inscrire l’un des formateurs disponibles, utilisez la `Add{Type}Console` méthode d’extension correspondante :

| Types disponibles | Méthode d’inscription de type |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a>Simple

Pour utiliser le `Simple` formateur de console, inscrivez-le auprès des `AddSimpleConsole` éléments suivants :

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

Dans l’exemple de code source précédent, le <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formateur a été inscrit. Il offre aux journaux la possibilité d’encapsuler des informations telles que le temps et le niveau de journalisation dans chaque message de journal, mais permet également l’incorporation et la mise en retrait de couleurs ANSI des messages.

### <a name="systemd"></a>SystemD

Le <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> Journal de console :

- Utilise le format et les niveaux de gravité du journal « syslog »
- Ne met **pas** en forme les messages avec des couleurs
- Enregistre toujours les messages sur une seule ligne

Cela est souvent utile pour les conteneurs, qui utilisent souvent la `Systemd` journalisation de la console. Avec .NET 5, le `Simple` Journal de console permet également une version compacte qui se connecte sur une seule ligne et permet également de désactiver les couleurs comme indiqué dans un exemple précédent.

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a>Json

Pour écrire des journaux au format JSON, le module de formatage de la `Json` console est utilisé. L’exemple de code source montre comment un ASP.NET Core application peut l’inscrire. À l’aide du `webapp` modèle, créez une nouvelle ASP.net Core application avec la commande [dotnet New](../tools/dotnet-new.md) :

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

Quand vous exécutez l’application, à l’aide du code du modèle, vous recevez le format de journal par défaut ci-dessous :

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

Par défaut, le module `Simple` de formatage du journal de la console est sélectionné avec la configuration par défaut. Pour modifier cela, appelez `AddJsonConsole` dans *Program.cs*:

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

Exécutez à nouveau l’application, avec la modification ci-dessus, le message de journal est désormais au format JSON :

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> Le module de `Json` formatage de la console, par défaut, journalise chaque message sur une seule ligne. Pour le rendre plus lisible lors de la configuration du formateur, affectez <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> à la valeur `true` .

## <a name="set-formatter-with-configuration"></a>Définir le formateur avec la configuration

Les exemples précédents ont montré comment inscrire un formateur par programme. Vous pouvez également effectuer cette opération avec la [configuration](configuration.md). Prenons l’exemple de code source précédent de l’application Web, si vous mettez à jour le *appsettings.jssur* le fichier au lieu `ConfigureLogging` d’appeler dans le fichier *Program.cs* , vous pouvez avoir le même résultat. Le fichier mis à jour `appsettings.json` configure le formateur comme suit :

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

Les deux valeurs de clés qui doivent être définies sont `"FormatterName"` et `"FormatterOptions"` . Si un formateur avec la valeur définie pour `"FormatterName"` est déjà inscrit, ce formateur est sélectionné, et ses propriétés peuvent être configurées tant qu’elles sont fournies en tant que clé à l’intérieur du `"FormatterOptions"` nœud. Les noms de formateur prédéfinis sont réservés sous <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> :

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a>Implémenter un formateur personnalisé

Pour implémenter un formateur personnalisé, vous devez :

- Créer une sous-classe de <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> , qui représente votre formateur personnalisé
- Inscrire votre formateur personnalisé avec
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

Créez une méthode d’extension pour la gérer pour vous :

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

Les `CustomOptions` sont définis comme suit :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

Dans le code précédent, les options sont une sous-classe de <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> .

L' `AddConsoleFormatter` API :

- Inscrit une sous-classe de `ConsoleFormatter`
- Gère la configuration :
  - Utilise un jeton de modification pour synchroniser les mises à jour, en fonction du [modèle d’options](options.md)et de l’interface [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601)

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

Définissez une `CustomerFormatter` sous-classe de `ConsoleFormatter` :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

L' `CustomFormatter.Write<TState>` API précédente dicte le texte qui est encapsulé autour de chaque message de journal. Une norme `ConsoleFormatter` doit pouvoir habiller au minimum les étendues, les horodatages et le niveau de gravité des journaux. En outre, vous pouvez encoder les couleurs ANSI dans les messages du journal et fournir également les mises en retrait souhaitées. L’implémentation du n’a `CustomFormatter.Write<TState>` pas ces fonctionnalités.

Pour plus d’informations sur la personnalisation de la mise en forme, consultez les implémentations existantes dans l' `Microsoft.Extensions.Logging.Console` espace de noms :

- [SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).
- [SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a>Implémenter une mise en forme personnalisée des couleurs

Pour activer correctement les fonctionnalités de couleur dans votre formateur de journalisation personnalisé, vous pouvez étendre le <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> comme il dispose d’une <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> propriété qui peut être utile pour activer les couleurs dans les journaux.

Créez un `CustomColorOptions` qui dérive de `SimpleConsoleFormatterOptions` :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

Ensuite, écrivez des méthodes d’extension dans une `TextWriterExtensions` classe qui permettent d’incorporer facilement des couleurs codées ANSI dans les messages de journal mis en forme :

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

Un formateur de couleurs personnalisé qui gère l’application de couleurs personnalisées peut être défini comme suit :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

Lorsque vous exécutez l’application, les journaux affichent le `CustomPrefix` message dans la couleur verte lorsque `FormatterOptions.ColorBehavior` est `Enabled` .

> [!NOTE]
> Lorsque <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> est `Disabled` , les messages de journalisation n’interprètent _pas_ les codes de couleur ANSI incorporés dans les messages de journal. Au lieu de cela, ils génèrent le message brut. Prenons l’exemple suivant :
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> Cela génère la chaîne textuelle et n’est _pas_ colorée.
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a>Voir aussi

- [Journalisation dans .NET](logging.md)
- [Implémenter un fournisseur de journalisation personnalisé dans .NET](custom-logging-provider.md)
- [Journalisation hautes performances dans .NET](high-performance-logging.md)
