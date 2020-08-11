---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062421"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Pas de détection de suffixe A/W sur les plateformes non-Windows

Les runtimes .NET n’ajoutent plus `A` `W` de suffixe ou pour les noms d’exportation de fonction lors de la détection pour P/Invoke sur les plateformes non-Windows.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 4

#### <a name="change-description"></a>Description de la modification

[Windows a une convention](/windows/win32/intl/conventions-for-function-prototypes) d’ajout d' `A` un `W` suffixe ou à SDK Windows noms de fonction, qui correspondent respectivement à la page de codes Windows et aux versions Unicode.

Dans les versions précédentes de .NET, les runtimes CoreCLR et mono ajoutaient `A` un `W` suffixe ou au nom de l’exportation lors de la détection d’exportation pour P/Invoke *sur toutes les plateformes*.

Dans .NET 5,0 et versions ultérieures, `A` un `W` suffixe ou est ajouté au nom d’exportation lors de la découverte de l’exportation *sur Windows uniquement*. Sur les plateformes UNIX, le suffixe n’est pas ajouté. La sémantique des deux runtimes sur la plate-forme Windows reste inchangée.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée pour simplifier la détection inter-plateformes. La surcharge ne doit pas être encourue, étant donné que les plateformes non-Windows ne contiennent pas cette sémantique.

#### <a name="recommended-action"></a>Action recommandée

Pour atténuer la modification, vous pouvez ajouter manuellement le suffixe souhaité sur les plateformes non-Windows. Par exemple :

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a>Category

Interop

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
