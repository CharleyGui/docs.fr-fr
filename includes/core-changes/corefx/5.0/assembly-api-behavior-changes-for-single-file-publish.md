---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955553"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>Modifications du comportement des API liées à l’assembly pour le format de publication à fichier unique

Plusieurs API liées à l’emplacement des fichiers d’un assembly ont des modifications de comportement lorsqu’elles sont appelées dans un format de publication à fichier unique.

#### <a name="change-description"></a>Description de la modification

Dans la publication de fichier unique pour .NET 5,0 et versions ultérieures, les assemblys regroupés sont chargés à partir de la mémoire au lieu d’être extraits sur le disque. Pour les applications publiées sur un seul fichier, cela signifie que certaines API liées à l’emplacement retournent des valeurs différentes sur .NET 5,0 et versions ultérieures par rapport aux versions précédentes de .NET. Les modifications sont les suivantes :

| API | Versions précédentes | .NET 5,0 et versions ultérieures |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | Retourne le chemin du fichier DLL extrait | Retourne une chaîne vide pour les assemblys regroupés |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | Retourne le chemin du fichier DLL extrait | Lève une exception pour les assemblys regroupés |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | Retourne `null` pour les assemblys regroupés | Lève une exception pour les assemblys regroupés |
| `Environment.GetCommandLineArgs()[0]` | La valeur est le nom de la DLL de point d’entrée | La valeur est le nom de l’exécutable hôte |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | La valeur est le répertoire d’extraction temporaire | La valeur est le répertoire conteneur du fichier exécutable de l’hôte |

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="recommended-action"></a>Action recommandée

Évitez les dépendances sur l’emplacement de fichier des assemblys lors de la publication sous la forme d’un fichier unique.

#### <a name="category"></a>Category

- Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
