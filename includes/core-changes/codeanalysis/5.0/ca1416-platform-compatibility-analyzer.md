---
ms.openlocfilehash: 4a7616d2ffaabab5279342ebc1082c93a174a52d
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406169"
---
### <a name="ca1416-platform-compatibility"></a>CA1416 : compatibilité de la plateforme

La règle de l’analyseur de code .NET [CA1416](/visualstudio/code-quality/ca1416) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour les appels aux API spécifiques à la plateforme à partir des sites d’appel qui ne vérifient pas le système d’exploitation.

#### <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md). Plusieurs de ces règles sont activées, par défaut, y compris [CA1416](/visualstudio/code-quality/ca1416). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération. La règle CA1416 vous informe lorsque vous utilisez des API spécifiques à la plateforme à partir de emplacements où le contexte de plateforme n’est pas vérifié.

La règle [CA1416](/visualstudio/code-quality/ca1416), l’analyseur de compatibilité de la plateforme, fonctionne à la main avec d’autres fonctionnalités nouvelles dans .net 5,0. .NET 5,0 introduit les <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> et <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> , qui vous permettent de spécifier les plateformes sur lesquelles une API *est* ou *n’est pas* prise en charge. En l’absence de ces attributs, une API est supposée être prise en charge sur toutes les plateformes. Ces attributs ont été appliqués aux API spécifiques à la plateforme dans les bibliothèques .NET de base.

Dans les projets qui ciblent des plateformes pour lesquelles les API qu’ils utilisent ne sont pas disponibles, la règle [CA1416](/visualstudio/code-quality/ca1416) signale tous les appels d’API spécifiques à la plateforme où le contexte de plateforme n’est pas vérifié. La plupart des API qui sont maintenant décorées avec les <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributs et lèvent des <xref:System.PlatformNotSupportedException> exceptions lorsqu’elles sont appelées sur un système d’exploitation non pris en charge. Maintenant que ces API sont marquées comme spécifiques à la plateforme, la règle [CA1416](/visualstudio/code-quality/ca1416) vous aide à éviter les exceptions d’exécution <xref:System.PlatformNotSupportedException> en ajoutant des vérifications du système d’exploitation à vos sites d’appel.

#### <a name="examples"></a>Exemples

- La <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> méthode est uniquement prise en charge sur Windows et est décorée avec `[SupportedOSPlatform("windows")]` . Le code suivant produira un avertissement CA1416 au moment de la génération si le projet [cible](../../../../docs/standard/frameworks.md) `net5.0` (mais pas `net5.0-windows` ). Pour les actions que vous pouvez entreprendre pour éviter l’avertissement, consultez [action recommandée](#recommended-action).

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- La <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> méthode n’est pas prise en charge dans le navigateur et est décorée avec `[UnsupportedOSPlatform("browser")]` . Le code suivant produira un avertissement CA1416 au moment de la génération si le projet prend en charge la plateforme du navigateur.

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - Les projets d’assembly Web éblouissant et les projets de bibliothèque de classes Razor incluent automatiquement la prise en charge des navigateurs.
  > - Pour ajouter manuellement le navigateur en tant que plateforme prise en charge pour votre projet, ajoutez l’entrée suivante à votre fichier projet :
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

#### <a name="version-introduced"></a>Version introduite

5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous que les API spécifiques à la plateforme sont appelées uniquement lorsque le code s’exécute sur une plateforme appropriée. Vous pouvez vérifier le système d’exploitation actuel à l’aide de l’une des `Is<Platform>` méthodes de la <xref:System.OperatingSystem?displayProperty=nameWithType> classe, par exemple, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> , avant d’appeler une API spécifique à la plateforme.

Vous pouvez utiliser l’une des `Is<Platform>` méthodes dans la condition d’une `if` instruction :

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

Ou, si vous ne souhaitez pas la surcharge d’une `if` instruction supplémentaire au moment de l’exécution, appelez à la <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> place :

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

Si vous créez une bibliothèque, vous pouvez marquer votre API comme étant spécifique à la plateforme. Dans ce cas, la charge liée à la vérification des exigences incombe à vos appelants. Vous pouvez marquer des méthodes ou des types spécifiques ou un assembly entier.

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

Si vous ne souhaitez pas corriger tous vos sites d’appel, vous pouvez choisir l’une des options suivantes pour supprimer l’avertissement :

- Pour supprimer CA1416 de règle, vous pouvez utiliser `#pragma` ou l’indicateur [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) du compilateur, ou en [définissant la gravité de la règle](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) sur `none` dans un fichier. editorconfig.

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Category

- Analyse du code
- Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

Pour la plateforme Windows :

- Toutes les API figurant dans <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

Pour la plateforme de l’assembly éblouissant :

- Toutes les API figurant dans <https://github.com/dotnet/runtime/issues/41087> .

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a>Voir aussi

- [CA1416 : Valider la compatibilité de la plateforme](/visualstudio/code-quality/ca1416)
- [Analyseur d’API .NET](../../../../docs/standard/analyzers/api-analyzer.md)
