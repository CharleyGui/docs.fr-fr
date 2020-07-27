---
title: Formats de chemin de fichier sur les systèmes Windows
description: Dans cet article, Découvrez les formats de chemin d’accès aux fichiers sur les systèmes Windows, tels que les chemins DOS traditionnels, les chemins d’accès de périphérique DOS et les chemins d’accès UNC (Universal Naming Convention).
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: 5eb9d5127dffd2e80349352ad7a4b57f8848d56b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165797"
---
# <a name="file-path-formats-on-windows-systems"></a>Formats de chemin de fichier sur les systèmes Windows

Dans l’espace de noms <xref:System.IO>, les membres de nombreux types incluent un paramètre `path` qui vous permet de spécifier un chemin absolu ou relatif à une ressource de système de fichiers. Ce chemin est ensuite passé aux [API de système de fichiers Windows](/windows/desktop/fileio/file-systems). Cette rubrique décrit les formats de chemins de fichier que vous pouvez utiliser dans les systèmes Windows.

## <a name="traditional-dos-paths"></a>Chemins DOS traditionnels

Un chemin DOS standard peut être constitué de trois composants :

- Une lettre de volume ou de lecteur suivie du séparateur de volumes (`:`).
- Un nom de répertoire. Le [caractère de séparation de répertoires](<xref:System.IO.Path.DirectorySeparatorChar>) sépare les sous-répertoires au sein de la hiérarchie de répertoires imbriqués.
- Un nom de fichier facultatif. Le [caractère de séparation de répertoires](<xref:System.IO.Path.DirectorySeparatorChar>) sépare le chemin et le nom de fichier.

Si les trois composants sont présents, le chemin est absolu. Si aucune lettre de lecteur ou de volume n’est spécifiée et que le [caractère de séparation de répertoires](<xref:System.IO.Path.DirectorySeparatorChar>) précède les noms de répertoires, le chemin est relatif à la racine du lecteur actif. Sinon, le chemin est relatif au répertoire actif. Le tableau suivant présente certains chemins de répertoire et de fichier.

|Path  |Description  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Chemin de fichier absolu à partir de la racine du lecteur C:. |
| `\Program Files\Custom Utilities\StringFinder.exe` | Chemin absolu à partir de la racine du lecteur actif. |
| `2018\January.xlsx` | Chemin relatif à un fichier dans un sous-répertoire du répertoire actif. |
| `..\Publications\TravelBrochure.pdf` | Chemin relatif à un fichier dans répertoire qui est un pair du répertoire actif. |
| `C:\Projects\apilibrary\apilibrary.sln` | Chemin absolu à un fichier à partir de la racine du lecteur C:. |
| `C:Projects\apilibrary\apilibrary.sln` | Chemin relatif à partir du répertoire actif du lecteur C:. |

> [!IMPORTANT]
> Notez la différence entre les deux derniers chemins. Les deux chemins spécifient le spécificateur de volume facultatif (C: dans les deux cas), mais le premier commence par la racine du volume spécifié, contrairement au second. Le premier chemin est donc un chemin absolu à partir du répertoire racine du lecteur C:, tandis que le second est un chemin relatif à partir du répertoire actif du lecteur C:. L’utilisation involontaire de la deuxième forme à la place de la première est une source courante de bogues impliquant des chemins de fichier Windows.

Pour déterminer si un chemin de fichier est complet (autrement dit, si le chemin est indépendant du répertoire actif et qu’il reste inchangé quand le répertoire actif change), appelez la méthode <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType>. Notez qu’un tel chemin peut inclure des segments de répertoire relatifs (`.` et `..`) et toujours être complet si le chemin résolu pointe toujours vers le même emplacement.

L’exemple suivant illustre la différence entre les chemins absolus et relatifs. Il part du principe que le répertoire D:\FY2018\ existe et que vous n’avez défini aucun répertoire actif pour D:\ à partir de l’invite de commandes avant d’exécuter l’exemple.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>Chemins UNC

Les chemins respectant la convention d’affectation de noms (UNC), qui sont utilisés pour accéder aux ressources réseau, ont le format suivant :

- Un nom de serveur ou d’hôte, précédé de \\\\. Le nom du serveur peut être un nom d’ordinateur NetBIOS ou une adresse IP/FQDN (IPv4 et IPv6 sont pris en charge).
- Un nom de partage, séparé du nom d’hôte par \\. Ensemble, le serveur et le partage forment le volume.
- Un nom de répertoire. Le [caractère de séparation de répertoires](<xref:System.IO.Path.DirectorySeparatorChar>) sépare les sous-répertoires au sein de la hiérarchie de répertoires imbriqués.
- Un nom de fichier facultatif. Le [caractère de séparation de répertoires](<xref:System.IO.Path.DirectorySeparatorChar>) sépare le chemin et le nom de fichier.

Voici quelques exemples de chemins UNC :

|Path  |Description  |
| -- | -- |
| `\\system07\C$\` | Répertoire racine du lecteur C: sur `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Fichier Foo.txt dans le répertoire Test du volume \\\\Server2\\Share.|

Les chemins UNC doivent toujours être complets. Ils peuvent inclure des segments de répertoire relatifs (`.` et `..`), mais il doivent faire partie d’un chemin complet. Pour utiliser des chemins relatifs, vous devez impérativement mapper un chemin UNC à une lettre de lecteur.

## <a name="dos-device-paths"></a>Chemins de périphérique DOS

Le système d’exploitation Windows a un modèle objet unifié qui pointe vers toutes les ressources, notamment les fichiers. Ces chemins d’objet sont accessibles à partir de la fenêtre de console et sont exposés à la couche Win32 par le biais d’un dossier spécial de liens symboliques mappés aux chemins DOS et UNC hérités. Ce dossier spécial est accessible par le biais d’un chemin de périphérique DOS, dont la syntaxe est l’une des suivantes :

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

En plus d’identifier un lecteur par sa lettre de lecteur, vous pouvez identifier un volume à l’aide de son GUID de volume. Cela prend la forme :

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> La syntaxe des chemins de périphérique DOS est prise en charge sur les implémentations .NET s’exécutant sur Windows à compter de .NET Core 1.1 et .NET Framework 4.6.2.

Le chemin de périphérique DOS comprend les composants suivants :

- Le spécificateur de chemin de périphérique (`\\.\` ou `\\?\`), qui identifie le chemin comme chemin de périphérique DOS.

   > [!NOTE]
   > Le spécificateur `\\?\` est pris en charge dans toutes les versions de .NET Core et dans le .NET Framework à compter de la version 4.6.2.

- Un lien symbolique vers le « vrai » objet d’appareil (C: dans le cas d’un nom de lecteur, ou Volume{b75e2c83-0000-0000-0000-602f00000000} dans le cas d’un GUID de volume).

   Le premier segment du chemin de périphérique DOS après le spécificateur de chemin de périphérique identifie le volume ou le lecteur. (Par exemple, `\\?\C:\` et `\\.\BootPartition\`.)

   Il existe un lien spécifique pour les chemins UNC. Celui-ci s’appelle, sans surprise, `UNC`. Par exemple :

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Pour les chemins UNC de périphérique, la partie serveur/partage forme le volume. Par exemple, dans `\\?\server1\e:\utilities\\filecomparer\`, la partie serveur/partage est server1\utilities. Ceci est important quand vous appelez une méthode comme <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> avec des segments de répertoire relatifs ; il est impossible de naviguer au-delà du volume.

Par définition, les chemins de périphérique DOS sont complets. Les segments de répertoire relatifs (`.` et `..`) ne sont pas autorisés. Les répertoires actifs ne font jamais partie de ce type de chemin.

## <a name="example-ways-to-refer-to-the-same-file"></a>Exemple : Comment faire référence au même fichier

L’exemple suivant illustre quelques-unes des méthodes vous permettant de faire référence à un fichier à l’aide des API dans l’espace de noms <xref:System.IO>. L’exemple instancie un objet <xref:System.IO.FileInfo> et utilise ses propriétés <xref:System.IO.FileInfo.Name> et <xref:System.IO.FileInfo.Length> pour afficher le nom et la longueur du fichier.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalisation des chemins d’accès

Presque tous les chemins passés aux API Windows sont normalisés. Durant la normalisation, Windows effectue les étapes suivantes :

- Identifie le chemin.
- Applique le répertoire actif aux chemins partiels (relatifs).
- Applique une mise en forme canonique aux séparateurs de composants et de répertoires.
- Évalue les composants des répertoires relatifs (`.` pour le répertoire actif et `..` pour le répertoire parent).
- Supprime certains caractères.

Cette normalisation se produit implicitement, mais vous pouvez l’effectuer explicitement en appelant la méthode <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>, qui inclut dans un wrapper un appel à la [fonction GetFullPathName()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea). Vous pouvez également appeler directement la [fonction GetFullPathName()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) Windows à l’aide de P/Invoke.

### <a name="identify-the-path"></a>Identifier le chemin

La première étape de normalisation d’un chemin consiste à identifier le type du chemin. Les chemins appartiennent à l’une des catégories suivantes :

- Chemins de périphérique : commencent par deux séparateurs et un point d’interrogation ou un point (`\\?` ou `\\.`).
- Chemins UNC : commencent par deux séparateurs sans point d’interrogation ou point.
- Chemins DOS complets : commencent par une lettre de lecteur, un séparateur de volumes et un séparateur de composants (`C:\`).
- Chemins désignant un périphérique hérité (`CON`, `LPT1`).
- Chemins relatifs à la racine du lecteur actif : commencent par un séparateur de composants unique (`\`).
- Chemins relatifs au répertoire actif d’un lecteur spécifié : commencent par une lettre de lecteur, un séparateur de volumes et aucun séparateur de composants (`C:`).
- Chemins relatifs au répertoire actif : ils commencent par autre chose (`temp\testfile.txt`).

Le type du chemin détermine si un répertoire actif est appliqué ou non d’une certaine façon. Il détermine également la « racine » du chemin.

### <a name="handle-legacy-devices"></a>Gérer les appareils hérités

Si le chemin est un périphérique DOS hérité comme `CON`, `COM1` ou `LPT1`, il est converti en chemin de périphérique (préfixe `\\.\` ajouté) et retourné.

Un chemin qui commence par un nom de périphérique hérité est toujours interprété comme périphérique hérité par la méthode <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType>. Par exemple, le chemin de périphérique DOS pour `CON.TXT` est `\\.\CON`, et celui pour `COM1.TXT\file1.txt` est `\\.\COM1`.

### <a name="apply-the-current-directory"></a>Appliquer le répertoire actif

Si un chemin n’est pas complet, Windows applique à celui-ci le répertoire actif. Le répertoire actif n’est pas appliqué aux chemins UNC et de périphérique. Il n’est pas non plus appliqué à un lecteur complet avec le séparateur C:\\.

Si le chemin commence par un séparateur de composant unique, le lecteur du répertoire actif est appliqué. Par exemple, si le chemin de fichier est `\utilities` et le répertoire actif `C:\temp\`, la normalisation produit `C:\utilities`.

Si le chemin commence par une lettre de lecteur, comprend un séparateur de volumes, mais ne contient aucun séparateur de composants, le dernier répertoire actif défini à partir de l’interface de commande pour le lecteur spécifié est appliqué. Si le dernier répertoire actif n’a pas été défini, seul le lecteur est appliqué. Par exemple, si le chemin de fichier est `D:sources`, le répertoire actif `C:\Documents\` et le dernier répertoire actif sur le lecteur D: `D:\sources\`, le résultat est `D:\sources\sources`. Ces chemins « relatifs au lecteur » sont une source commune d’erreurs de logique qui affectent les programmes et les scripts. Il est évidemment incorrect d’assumer qu’un chemin commençant par une lettre et un signe deux-points n’est pas relatif.

Si le chemin commence par un élément autre qu’un séparateur, le lecteur et le répertoire actifs sont appliqués. Par exemple, si le chemin est `filecompare` et le répertoire actif `C:\utilities\`, le résultat est `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Les chemins relatifs sont dangereux dans les applications multithreads (c’est-à-dire dans la plupart des applications), car le répertoire actif est un paramètre par processus. N’importe quel thread peut changer le répertoire actif à tout moment. À compter de .NET Core 2.1, vous pouvez appeler la méthode <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> pour obtenir un chemin absolu à partir d’un chemin relatif et le chemin de base (répertoire actif) par rapport auquel vous souhaitez le résoudre.

### <a name="canonicalize-separators"></a>Canonicaliser les séparateurs

Toute barre oblique (`/`) est convertie en séparateur Windows standard, à savoir la barre oblique inverse (`\`). Toute série de barres obliques après les deux premières barres obliques est réduite en barre oblique unique.

### <a name="evaluate-relative-components"></a>Évaluer les composants relatifs

À mesure que le chemin est traité, tout composant ou segment constitué d’un point unique ou double (`.` ou `..`) est évalué :

- Pour un point unique, le segment actif est supprimé, car il fait référence au répertoire actif.

- Pour un point double, le segment actif et le segment parent sont supprimés, car il fait référence au répertoire parent.

   Les répertoires parents sont uniquement supprimés s’ils ne sont pas situés au-delà de la racine du chemin. La racine du chemin varie selon le type de chemin. Il s’agit du lecteur (`C:\`) pour les chemins DOS, du serveur/partage pour les chemins UNC (`\\Server\Share`) et du préfixe du chemin de périphérique pour les chemins de périphérique (`\\?\` ou `\\.\`).

### <a name="trim-characters"></a>Supprimer les caractères

Outre les séries de séparateurs et de segments relatifs supprimés précédemment, d’autres caractères sont supprimés durant la normalisation :

- Si un segment se termine par un point unique, celui-ci est supprimé. (Un segment constitué d’un point unique ou double est normalisé à l’étape précédente. Un segment constitué de trois ou quatre points n’est pas normalisé, car il s’agit d’un nom de fichier/répertoire valide.)

- Si le chemin ne se termine pas par un séparateur, tous les points et espaces (U+0020) de fin sont supprimés. Si le dernier segment est simplement un point simple ou double, il relève de la règle des composants relatifs ci-dessus.

   Cette règle signifie que vous pouvez créer un nom de répertoire avec un espace de fin en ajoutant un séparateur de fin après l’espace.

   > [!IMPORTANT]
   > **Ne créez jamais** un répertoire ou un nom de fichier avec un espace de fin. Les espaces de fin peuvent rendre l’accès à un répertoire difficile voire impossible, et il arrive fréquemment que des applications échouent quand vous tentez de gérer des répertoires ou des fichiers dont les noms comprennent des espaces de fin.

## <a name="skip-normalization"></a>Ignorer la normalisation

En règle générale, tout chemin passé à une API Windows est (effectivement) passé à la [fonction GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) et normalisé. Il existe toutefois une exception importante : un chemin de périphérique qui commence par un point d’interrogation et non un point. À moins qu’il ne commence exactement par `\\?\` (notez l’utilisation de la barre oblique inverse canonique), le chemin est normalisé.

Pourquoi ignorer la normalisation ? Voici les trois raisons principales :

1. Accéder aux chemins normalement indisponibles, mais autorisés. Par exemple, il est impossible d’accéder à un fichier ou à un répertoire appelé `hidden.` d’une autre manière.

1. Améliorer le niveau de performance en ignorant la normalisation précédemment effectuée.

1. Sur le .NET Framework uniquement, ignorer la vérification de la longueur du chemin (`MAX_PATH`) et autoriser les chemins de plus de 259 caractères. La plupart des API autorisent ceci, à quelques exceptions près.

> [!NOTE]
> .NET Core gère implicitement les chemins longs et n’effectue pas la vérification `MAX_PATH`. La vérification `MAX_PATH` s’applique uniquement au .NET Framework.

La seule différence entre les deux syntaxes de chemin de périphérique tient au fait que vous pouvez ignorer la normalisation et les vérifications de la longueur maximale des chemins ; sinon, elles sont identiques. Soyez prudent si vous choisissez d’ignorer la normalisation, car vous pouvez facilement créer des chemins difficiles à gérer pour les applications « normales ».

Les chemins qui commencent par `\\?\` sont toujours normalisés si vous les passez explicitement à la [fonction GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Vous pouvez passer des chemins de plus de `MAX_PATH` caractères à [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) sans `\\?\` . Elle prend en charge les chemins de longueur arbitraire jusqu’à la taille de chaîne maximale gérée par Windows.

## <a name="case-and-the-windows-file-system"></a>Casse et système de fichiers Windows

Le fait que les noms de chemin et de répertoire ne respectent pas la casse est une particularité du système de fichiers Windows que les développeurs et utilisateurs d’autres systèmes d’exploitation trouvent déroutante. Autrement dit, les noms de répertoire et de fichier reflètent la casse des chaînes utilisée au moment de leur création. Par exemple, l’appel de méthode

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

crée un répertoire nommé TeStDiReCtOrY. Si vous renommez un répertoire ou un fichier pour changer sa casse, le nom du répertoire ou du fichier reflète la casse de la chaîne utilisée au moment du renommage. Par exemple, le code suivant renomme un fichier nommé test.txt en Test.txt :

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Toutefois, les comparaisons des noms de répertoire et de fichier ne respectent pas la casse. Si vous recherchez un fichier nommé « test.txt », les API du système de fichiers .NET ignorent la casse dans la comparaison. « Test.txt », « TEST.TXT », « test.TXT » et toute autre combinaison de lettres majuscules et minuscules correspond à « test.txt ».
