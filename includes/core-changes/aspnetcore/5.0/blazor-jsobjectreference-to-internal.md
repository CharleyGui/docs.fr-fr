---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077590"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Éblouissant : les types JSObjectReference et JSInProcessObjectReference sont devenus internes

Les nouveaux `Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` types et introduits dans ASP.net Core 5,0 RC1 ont été marqués comme `internal` .

#### <a name="version-introduced"></a>Version introduite

5,0 RC2

#### <a name="old-behavior"></a>Ancien comportement

Un `JSObjectReference` peut être obtenu à partir d’un appel JavaScript Interop via `IJSRuntime` . Par exemple :

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>Nouveau comportement

`JSObjectReference` utilise le modificateur d’accès [interne](../../../../docs/csharp/language-reference/keywords/internal.md) . L' `public` `IJSObjectReference` interface doit être utilisée à la place. Par exemple :

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` était également marqué comme `internal` et a été remplacé par `IJSInProcessObjectReference` .

#### <a name="reason-for-change"></a>Motif de modification

La modification rend la fonctionnalité d’interopérabilité JavaScript plus cohérente avec d’autres modèles dans éblouissant. `IJSObjectReference` est analogue à `IJSRuntime` dans le sens où il a un objectif similaire et possède des méthodes et des extensions similaires.

#### <a name="recommended-action"></a>Action recommandée

Remplacez les occurrences de `JSObjectReference` et de `JSInProcessObjectReference` par `IJSObjectReference` et `IJSInProcessObjectReference` , respectivement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
