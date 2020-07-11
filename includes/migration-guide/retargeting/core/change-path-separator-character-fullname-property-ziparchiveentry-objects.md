---
ms.openlocfilehash: f87d0dbeda6094bd745f5b580772b1161f30d0d5
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218298"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>Changement du caractère séparateur de chemin dans la propriété FullName des objets ZipArchiveEntry

#### <a name="details"></a>Détails

Pour les applications qui ciblent le .NET Framework 4.6.1 et les versions ultérieures, le caractère de séparation du chemin d’accès est passé d’une barre oblique inverse (« \\ ») à une barre oblique (« / ») dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName> propriété des <xref:System.IO.Compression.ZipArchiveEntry> objets créés par les surcharges de la <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> méthode. L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.<br />La décompression d’un fichier zip créé par une application qui cible une version antérieure du .NET Framework sur les systèmes d’exploitation non-Windows, tels que les ordinateurs Macintosh, ne permet pas de conserver la structure de répertoire. Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse (« \\ ») et le nom de fichier. Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.

#### <a name="suggestion"></a>Suggestion

Impact de cette modification sur. Les fichiers ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans l' <xref:System.IO?displayProperty=nameWithType> espace de noms .NET Framework doivent être minimaux, puisque ces API peuvent gérer en toute transparence une barre oblique (« / ») ou une barre oblique inverse (« \\ ») comme séparateur de chemin.<br />Si cette modification n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration à la [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation `Switch.System.IO.Compression.ZipFile.UseBackslash` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

En outre, les applications qui ciblent des versions antérieures du .NET Framework mais s’exécutent sur le .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’activation `Switch.System.IO.Compression.ZipFile.UseBackslash`.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
