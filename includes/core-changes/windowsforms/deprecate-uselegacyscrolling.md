---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181830"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling non pris en charge

Le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir du .NET Framework 4.7.1, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité permettait aux développeurs de refuser les <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> indépendantes et. Le commutateur <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a restauré le comportement hérité, dans lequel est ignoré si le texte de contexte est présent et que le développeur doit utiliser <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> l’action sur le contrôle avant <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> l’action. Pour plus d’informations, consultez [ \<AppContextSwitchOverrides >, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .net Core, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
