---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614427"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Autoriser les caractères de contrôle bidirectionnels Unicode dans les URI

#### <a name="details"></a>Détails

Unicode spécifie plusieurs caractères de contrôle spéciaux utilisés pour définir l’orientation du texte. Dans les versions précédentes du .NET Framework, ces caractères n’étaient pas correctement supprimés de tous les URI, même s’ils étaient encodés en pourcentage. Pour mieux suivre la spécification [RFC 3987](https://tools.ietf.org/html/rfc3987), nous autorisons désormais ces caractères dans les URI. Si une URI en contient qui ne sont pas encodés, ils sont encodés en pourcentage. Si elle en contient qui sont encodés en pourcentage, ils sont laissés tels quels.

#### <a name="suggestion"></a>Suggestion

Pour les applications qui ciblent des versions du .NET Framework à partir de la version 4.7.2, la prise en charge des caractères bidirectionnels Unicode est activée par défaut. Si ce changement n’est pas souhaitable, vous pouvez le désactiver en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

Pour les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur .NET Framework versions 4.7.2 et ultérieures, la prise en charge des caractères bidirectionnels Unicode est désactivée par défaut. Vous pouvez l’activer en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=nameWithType>
