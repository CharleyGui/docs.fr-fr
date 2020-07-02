---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614446"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Vérifier que System.Uri utilise un jeu de caractères réservés cohérent

#### <a name="details"></a>Détails

Dans <xref:System.Uri?displayProperty=fullName>, certains caractères encodés en pourcentage qui étaient parfois décodés demeurent désormais systématiquement encodés. Cela se produit sur les propriétés et méthodes qui accèdent aux composants de chemin, de requête, de fragment ou d’informations utilisateur de l’URI. Le comportement change uniquement quand les deux conditions suivantes sont vraies :

- L’URI contient la forme encodée d’un des caractères réservés suivants : `:`, `'`, `(`, `)`, `!` ou `*`.
- L’URI contient un caractère non réservé encodé ou Unicode. Si les deux conditions ci-dessus sont remplies, les caractères réservés encodés demeurent encodés. Dans les versions précédentes du .NET Framework, ils sont décodés.

#### <a name="suggestion"></a>Suggestion

Pour les applications qui ciblent les versions du .NET Framework à partir de la version 4.7.2, le nouveau comportement de décodage est activé par défaut. Si ce changement n’est pas souhaitable, vous pouvez le désactiver en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

Pour les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur .NET Framework versions 4.7.2 et ultérieures, le nouveau comportement de décodage est désactivé par défaut. Vous pouvez l’activer en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la `<runtime>` section du fichier de configuration de l’application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=nameWithType>
