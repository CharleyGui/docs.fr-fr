---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614515"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle attend maintenant une valeur HWND

#### <a name="details"></a>Détails

La valeur <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>, introduite dans .NET Framework 2.0, permet à une application d’inscrire une valeur de handle de fenêtre parente, pour que toute interface utilisateur nécessaire pour accéder à la clé (par exemple, une invite de code confidentiel ou une boîte de dialogue de consentement) s’ouvre sous la forme d’un enfant modal de la fenêtre spécifiée. À partir des applications qui ciblent .NET Framework 4.7, une application Windows Forms peut définir la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> avec du code semblable au suivant :

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

Dans les versions précédentes du .NET Framework, la valeur devait être un <xref:System.IntPtr?displayProperty=fullName> représentant un emplacement en mémoire où se trouvait la valeur [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND). La définition de la propriété sur form.Handle sur Windows 7 et les versions antérieures n’avait aucun effet, mais sur Windows 8 et les versions ultérieures, cela entraîne un &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : Le paramètre est incorrect.&quot;

#### <a name="suggestion"></a>Suggestion

Les applications ciblant .NET Framework 4.7 ou ultérieur qui souhaitent inscrire une relation de fenêtre parente sont encouragées à utiliser la forme simplifiée :

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

Les utilisateurs qui avaient identifié que la bonne valeur à passer était l’adresse d’un emplacement de la mémoire qui détenait la valeur `form.Handle` peuvent refuser ce changement de comportement en définissant le commutateur AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` sur `true` :

- En définissant des commutateurs de compatibilité programmatiquement sur AppContext, comme expliqué [ici](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).
- En ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

À l’inverse, les utilisateurs qui souhaitent adopter ce nouveau comportement sur le runtime .NET Framework 4.7 quand l’application se charge sur des versions antérieures du .NET Framework peuvent définir le commutateur AppContext sur `false`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,7         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
