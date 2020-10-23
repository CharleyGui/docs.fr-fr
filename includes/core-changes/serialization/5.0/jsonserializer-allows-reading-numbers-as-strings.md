---
ms.openlocfilehash: a93856aac97af5c392a2e4698d2da42413cfc3c8
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434988"
---
### <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a>Les applications ASP.NET Core autorisent la désérialisation des nombres entre guillemets

À compter de .NET 5,0, les applications ASP.NET Core utilisent les options de désérialisation par défaut comme spécifié par <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> . L' <xref:System.Text.Json.JsonSerializerDefaults.Web> ensemble d’options comprend la définition de la valeur <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> . Cette modification signifie que ASP.NET Core applications désérialiseront correctement les nombres représentés en tant que chaînes JSON, au lieu de lever une exception.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 3,0-3,1, <xref:System.Text.Json.JsonSerializer> lève une lors de la <xref:System.Text.Json.JsonException> désérialisation s’il rencontre un nombre entre guillemets dans une charge utile JSON. Les nombres entre guillemets sont utilisés pour mapper les propriétés de nombre dans les graphiques d’objets. Dans .NET Core 3,0-3,1, les nombres sont uniquement lus à partir de <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> jetons.

À compter de .NET 5,0, les nombres entre guillemets dans les charges utiles JSON sont considérés comme valides, par défaut, pour les applications ASP.NET Core. Aucune exception n’est levée pendant la désérialisation des nombres entre guillemets.

> [!TIP]
>
> - Il n’y a aucun changement de comportement pour la valeur par défaut, autonome <xref:System.Text.Json.JsonSerializer> ou <xref:System.Text.Json.JsonSerializerOptions> .
> - Il ne s’agit techniquement pas d’une modification avec rupture, car cela rend un scénario plus permissif au lieu de plus restrictif (autrement dit, il parvient à forcer un nombre à partir d’une chaîne JSON au lieu de lever une exception). Toutefois, étant donné qu’il s’agit d’un changement de comportement significatif qui affecte de nombreuses applications ASP.NET Core, il est documenté ici.
> - Les <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> méthodes d’extension et utilisent également le <xref:System.Text.Json.JsonSerializerDefaults.Web> jeu d’options de sérialisation.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="reason-for-change"></a>Motif de modification

Plusieurs utilisateurs ont demandé une option pour la gestion des nombres plus permissif dans <xref:System.Text.Json.JsonSerializer> . Ce feedback indique que de nombreux producteurs JSON (par exemple, les services sur le Web) émettent des chiffres entre guillemets. En autorisant la lecture des nombres entre guillemets (désérialisés), les applications .NET peuvent analyser ces charges utiles, par défaut, dans les contextes Web. La configuration est exposée par le biais de <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> afin que vous puissiez spécifier les mêmes options sur différentes couches d’application, par exemple, client, serveur et partagé.

#### <a name="recommended-action"></a>Action recommandée

Si cette modification est perturbatrice, par exemple, si vous dépendez de la gestion des nombres stricts pour la validation, vous pouvez réactiver le comportement précédent. Affectez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> à l’option la valeur <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .

Pour les applications ASP.NET Core MVC et API Web, vous pouvez configurer l’option dans à `Startup` l’aide du code suivant :

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

#### <a name="category"></a>Category

- ASP.NET Core
- Sérialisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
