---
title: 'Modification avec rupture : les chemins de code UTF-7 sont obsolètes'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les constructeurs UTF7 et UTF7Encoding sont obsolètes.
ms.date: 11/01/2020
ms.openlocfilehash: d58305f59a30cdf31a525c3789bd6497201c50ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760891"
---
# <a name="utf-7-code-paths-are-obsolete"></a>Les chemins d’accès de code UTF-7 sont obsolètes

L’encodage UTF-7 n’est plus utilisé dans les applications, et de nombreuses spécifications [interdisent désormais son utilisation](https://security.stackexchange.com/a/68609/3573) dans l’échange. Il est également occasionnellement [utilisé comme vecteur d’attaque dans les](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) applications qui ne prévoient pas la présence de données encodées en UTF-7. Microsoft vous avertit de l’utilisation de <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> car il ne fournit pas de détection d’erreurs.

Par conséquent, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont désormais obsolètes. De plus, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> et <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> ne vous autorisent plus à spécifier `UTF-7` .

## <a name="change-description"></a>Description de la modification

Auparavant, vous pouviez créer une instance de l’encodage UTF-7 à l’aide des <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> API. Par exemple :

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

En outre, une instance qui représente l’encodage UTF-7 a été énumérée par la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode, qui énumère toutes les <xref:System.Text.Encoding> instances inscrites sur le système.

À compter de .NET 5,0, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont obsolètes et produisent des avertissements `SYSLIB0001` (ou `MSLIB0001` dans les versions préliminaires). Toutefois, pour réduire le nombre d’avertissements reçus par les appelants lors de l’utilisation de la <xref:System.Text.UTF7Encoding> classe, le <xref:System.Text.UTF7Encoding> type lui-même n’est pas marqué comme obsolète.

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

En outre, les <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> méthodes traitent le nom d’encodage `utf-7` et la page de codes `65000` comme `unknown` . Le traitement de l’encodage `unknown` entraîne la levée par la méthode d’un <xref:System.ArgumentException> .

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

Enfin, la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode n’inclut pas l’encodage UTF-7 dans le <xref:System.Text.EncodingInfo> tableau qu’elle retourne. L’encodage est exclu, car il ne peut pas être instancié.

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a>Motif de modification

De nombreuses applications appellent `Encoding.GetEncoding("encoding-name")` avec une valeur de nom d’encodage fournie par une source non fiable. Par exemple, un client ou un serveur Web peut prendre la `charset` partie de l' `Content-Type` en-tête et passer directement la valeur à `Encoding.GetEncoding` sans la valider. Cela pourrait permettre à un point de terminaison malveillant de spécifier `Content-Type: ...; charset=utf-7` , ce qui pourrait entraîner un comportement Inpossible de l’application de réception.

En outre, la désactivation des chemins d’accès de code UTF-7 permet d’optimiser les compilateurs, tels que ceux utilisés par éblouissant, pour supprimer entièrement ces chemins de code de l’application résultante. Par conséquent, les applications compilées s’exécutent plus efficacement et occupent moins d’espace disque.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, vous n’avez aucune action à effectuer. Toutefois, pour les applications qui ont précédemment activé les chemins de code relatifs à UTF-7, prenez en compte les instructions qui suivent.

- Si votre application appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> avec des noms d’encodage inconnus fournis par une source non fiable :

  Au lieu de cela, comparez les noms d’encodage à une liste verte configurable. La liste verte configurable doit au minimum inclure le « UTF-8 » standard du secteur. En fonction de vos clients et des exigences réglementaires, vous devrez peut-être également autoriser les encodages spécifiques à une région, par exemple « GB18030 ».

  Si vous n’implémentez pas de liste verte, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> retourne tout <xref:System.Text.Encoding> ce qui est intégré au système ou qui est inscrit via un personnalisé <xref:System.Text.EncodingProvider> . Auditez les exigences de votre service afin de vérifier qu’il s’agit du comportement souhaité. UTF-7 continue d’être désactivé par défaut, sauf si votre application réactive le commutateur de compatibilité mentionné plus loin dans cet article.

- Si vous utilisez <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dans votre propre protocole ou format de fichier :

  Basculez vers à l’aide de <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou <xref:System.Text.UTF8Encoding> . UTF-8 est une norme de l’industrie qui est largement prise en charge dans les langages, les systèmes d’exploitation et les runtimes. L’utilisation d’UTF-8 facilite la maintenance à venir de votre code et le rend plus interopérable avec le reste de l’écosystème.

- Si vous comparez une <xref:System.Text.Encoding> instance à <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :

  Au lieu de cela, envisagez d’effectuer une vérification par rapport à la page de codes UTF-7 connue, qui est `65000` . En comparant à la page de codes, vous évitez l’avertissement et vous gérez également certains cas limites, par exemple si quelqu’un a appelé ou sous- `new UTF7Encoding()` classé le type.

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- Si vous devez utiliser <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> :

  Vous pouvez supprimer l' `SYSLIB0001` avertissement dans le code ou dans le fichier *. csproj* de votre projet.

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > La suppression `SYSLIB0001` désactive uniquement les <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> avertissements et obsoletion. Il ne désactive pas les autres avertissements et ne modifie pas le comportement des API comme <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

- Si vous devez prendre en charge `Encoding.GetEncoding("utf-7", ...)` :

  Vous pouvez réactiver la prise en charge de ce à l’aide d’un commutateur de compatibilité. Ce commutateur de compatibilité peut être spécifié dans le fichier *. csproj* de l’application ou dans un [fichier de configuration au moment](../../../run-time-config/index.md)de l’exécution, comme indiqué dans les exemples suivants.

  Dans le fichier *. csproj* de l’application :

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  Dans l'runtimeconfig.template.jsde l’application *sur* le fichier :

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > Si vous réactivez la prise en charge d’UTF-7, vous devez effectuer une révision de sécurité du code qui appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
