---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302705"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>Les API de globalisation utilisent des bibliothèques ICU sur Windows

.NET 5,0 et les versions ultérieures utilisent des bibliothèques [ICU (International Components for Unicode)](http://site.icu-project.org/home) pour la globalisation lorsqu’elles s’exécutent sur Windows 10 mai 2019 Update ou version ultérieure.

#### <a name="change-description"></a>Description de la modification

Auparavant, les bibliothèques .NET utilisaient des API [NLS (National Language Support)](/windows/win32/intl/national-language-support) pour la fonctionnalité de globalisation. Par exemple, les fonctions NLS ont été utilisées pour obtenir les données de culture, telles que les modèles de format de date et d’heure, de comparaison des chaînes et d’exécution de la casse des chaînes dans la culture appropriée.

À compter de .NET 5,0, si une application s’exécute sur Windows 10 mai 2019 Update ou version ultérieure, les bibliothèques .NET utilisent les API de globalisation [ICU](http://site.icu-project.org/home) . La mise à jour de Windows 10 mai 2019 et les versions ultérieures sont fournies avec la bibliothèque Native ICU. Si le Runtime .NET ne peut pas charger ICU, il utilise NLS à la place.

Cette modification a été introduite pour deux raisons :

- Les applications ont le même comportement de globalisation entre les plateformes, notamment Linux, macOS et Windows.
- Les applications peuvent contrôler le comportement de globalisation à l’aide de bibliothèques ICU personnalisées.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 Preview 4

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur. Toutefois, si vous souhaitez continuer à utiliser les API de globalisation NLS, vous pouvez définir un [commutateur au moment](../../../../docs/core/run-time-config/globalization.md#nls) de l’exécution pour revenir à ce comportement. Pour plus d’informations sur les commutateurs disponibles, consultez l’article présentation de la [globalisation et de la bibliothèque .net](/dotnet/standard/globalization-localization/globalization-icu) .

#### <a name="category"></a>Category

Globalisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- La plupart des types dans l' <xref:System.Globalization?displayProperty=fullName> espace de noms

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
