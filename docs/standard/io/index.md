---
title: E/S de fichiers et de flux - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3b3dcc3b96e12f89508f4d2708c5ab083516dba
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025500"
---
# <a name="file-and-stream-io"></a>Fichier et flux de données E/S

E/S de fichier et de flux (entrées/sorties) fait référence au transfert de données vers ou depuis un support de stockage. Dans le .NET Framework, les espaces de noms `System.IO` contiennent des types qui permettent la lecture et l'écriture, de façon synchrone ou asynchrone, sur les flux de données et les fichiers. Ces espaces de noms contiennent également les types qui exécutent la compression et la décompression sur les fichiers, et ceux qui permettent la communication via des canaux et des ports série.

Un fichier est une collection ordonnée et nommée d'octets ayant un stockage persistant. Lorsque vous travaillez sur des fichiers, vous manipulez des chemins d'accès aux répertoires, du stockage disque et des noms de fichiers et de répertoires. En revanche, un flux est une séquence d'octets que vous pouvez lire et écrire dans un magasin de stockage, qui peut être l'un des nombreux supports de stockage (par exemple, des disques ou de la mémoire). De même qu'il existe d'autres magasins de stockage que les disques, il existe d'autres flux que les flux de fichiers, tels que les flux de réseau, de mémoire et de canaux.

## <a name="files-and-directories"></a>Fichiers et répertoires

Utilisez les types de l'espace de noms <xref:System.IO?displayProperty=nameWithType> pour interagir avec les fichiers et les répertoires. Par exemple, obtenez et définissez les propriétés des fichiers et des répertoires, et extrayez les collections de fichiers et de répertoires en fonction de critères de recherche.

Pour les conventions de nommage des chemins et les nouvelles méthodes pour exprimer un chemin de fichier pour les systèmes Windows, notamment avec la syntaxe des appareils DOS prise en charge dans .NET Core 1.1 et ultérieur et le .NET Framework 4.6.2 et ultérieur, consultez [Formats de chemin de fichier sur les systèmes Windows](file-path-formats.md).

Voici quelques classes de fichiers et de répertoires couramment utilisées :

- <xref:System.IO.File> fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l'ouverture de fichiers et permet de créer un objet <xref:System.IO.FileStream>.

- <xref:System.IO.FileInfo> fournit des méthodes d'instance pour la création, la copie, la suppression, le déplacement et l'ouverture de fichiers et permet de créer un objet <xref:System.IO.FileStream>.

- <xref:System.IO.Directory> fournit des méthodes statiques pour la création, le déplacement et l'énumération dans les répertoires et les sous-répertoires.

- <xref:System.IO.DirectoryInfo> fournit des méthodes d'instance pour la création, le déplacement et l'énumération dans les répertoires et les sous-répertoires.

- <xref:System.IO.Path> fournit des méthodes et des propriétés pour le traitement des chaînes de répertoire entre plateformes.

Vous devez toujours fournir une gestion des exceptions robuste lors de l’appel des méthodes de système de fichiers. Pour plus d’informations, consultez [Gestion des erreurs E/S](handling-io-errors.md).

En plus d'utiliser ces classes, les utilisateurs de Visual Basic peuvent utiliser les méthodes et les propriétés fournies par la classe <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> pour l'E/S de fichier.

Voir [Guide pratique pour copier des répertoires](how-to-copy-directories.md), [Guide pratique pour créer un listing de répertoires](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100)) et [Guide pratique pour énumérer des répertoires et des fichiers](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Flux

La classe abstraite de base <xref:System.IO.Stream> prend en charge la lecture et l'écriture d'octets. Toutes les classes qui représentent des flux héritent de la classe <xref:System.IO.Stream>. La classe <xref:System.IO.Stream> et ses classes dérivées donnent une vue globale des sources de données et des référentiels, isolant ainsi le programmeur des détails propres au système d'exploitation et aux périphériques sous-jacents.

Les flux impliquent trois opérations fondamentales :

- Lecture : transfert de données d'un flux vers une structure de données tel qu'un tableau d'octets.

- Écriture : transfert de données d'une source de données dans un flux.

- Recherche : envoi d'une requête concernant la position actuelle dans un flux et modification de cette dernière.

Selon la source de données sous-jacente ou le référentiel, un flux peut prendre en charge certaines de ces capacités. Par exemple, la classe <xref:System.IO.Pipes.PipeStream> ne prend pas en charge la recherche. Les propriétés <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A> et <xref:System.IO.Stream.CanSeek%2A> d'un flux spécifient les opérations que le flux prend en charge.

Voici quelques classes de flux couramment utilisées :

- <xref:System.IO.FileStream> pour la lecture et l'écriture dans un fichier.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> pour la lecture et l'écriture dans un fichier d'un stockage isolé.

- <xref:System.IO.MemoryStream> pour la lecture et l'écriture dans la mémoire en tant que magasin de stockage.

- <xref:System.IO.BufferedStream> pour l'amélioration des performances de vos opérations de lecture et d'écriture.

- <xref:System.Net.Sockets.NetworkStream> pour la lecture et l'écriture sur vos sockets réseau.

- <xref:System.IO.Pipes.PipeStream> pour la lecture et l'écriture sur des canaux nommés ou anonymes.

- <xref:System.Security.Cryptography.CryptoStream> pour la liaison des flux de données aux transformations de chiffrement.

Pour obtenir un exemple d'utilisation de flux de façon asynchrone, consultez [E/S sur fichier asynchrones](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Lecteurs et writers

L'espace de noms <xref:System.IO?displayProperty=nameWithType> fournit également des types pour la lecture des caractères encodés à partir des flux et l'écriture des caractères encodés dans les flux. En général, les flux sont conçus pour l'entrée et la sortie d'octets. Les types lecteur et writer gèrent la conversion des caractères encodés en octets et inversement pour permettre au flux de terminer l'opération. Chaque classe de lecteur et writer est associée à un flux, qui peut être récupéré via la propriété `BaseStream` de la classe.

Voici quelques classes de lecteur et writer couramment utilisées :

- <xref:System.IO.BinaryReader> et <xref:System.IO.BinaryWriter> pour la lecture et l'écriture des types de données primitifs comme valeurs binaires.

- <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> pour la lecture et l'écriture à l'aide d'une valeur d'encodage pour convertir des caractères en octets et inversement.

- <xref:System.IO.StringReader> et <xref:System.IO.StringWriter> pour la lecture et l'écriture des caractères à partir de chaînes et inversement.

- <xref:System.IO.TextReader> et <xref:System.IO.TextWriter> servent de classes de base abstraites à d'autres lecteurs et writers qui lisent et écrivent des caractères et des chaînes, mais pas des données binaires.

Voir [Guide pratique pour lire du texte dans un fichier](how-to-read-text-from-a-file.md), [Guide pratique pour écrire du texte dans un fichier](how-to-write-text-to-a-file.md), [Guide pratique pour lire les caractères d’une chaîne](how-to-read-characters-from-a-string.md) et [Guide pratique pour écrire des caractères dans une chaîne](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Opérations d’E/S asynchrones

La lecture ou l'écriture de grandes quantités de données peut consommer beaucoup de ressources. Vous devez effectuer ces tâches de façon asynchrone si votre application doit rester réactive aux actions de l'utilisateur. Avec les opérations d'E/S synchrones, le thread d'interface utilisateur est bloqué jusqu'à ce que l'opération consommatrice de ressources soit terminée.  Utilisez des opérations d'E/S asynchrones lors du développement d'applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pour empêcher de donner l'impression que votre application a cessé de fonctionner.

Les membres asynchrones contiennent `Async` dans leurs noms, comme les méthodes <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> et <xref:System.IO.Stream.WriteAsync%2A>. Utilisez ces méthodes avec `async` et les mots clés `await`.

Pour plus d'informations, consultez [E/S de fichier asynchrone](asynchronous-file-i-o.md).

## <a name="compression"></a>Compression

La compression désigne le processus de réduction de la taille d'un fichier pour le stockage. La décompression consiste à extraire le contenu d'un fichier compressé afin qu'il soit dans un format utilisable. L'espace de noms <xref:System.IO.Compression?displayProperty=nameWithType> contient des types pour la compression et la décompression de fichiers et de flux.

Les classes suivantes sont fréquemment utilisées lors de la compression et de la décompression de fichiers et de flux :

- <xref:System.IO.Compression.ZipArchive> pour la création et l'extraction des entrées de l'archive zip.

- <xref:System.IO.Compression.ZipArchiveEntry> pour la représentation d'un fichier compressé.

- <xref:System.IO.Compression.ZipFile> pour la création, l'extraction et l'ouverture d'un package compressé.

- <xref:System.IO.Compression.ZipFileExtensions> pour la création et l'extraction des entrées dans un package compressé.

- <xref:System.IO.Compression.DeflateStream> pour la compression et la décompression des flux en utilisant l'algorithme Deflate.

- <xref:System.IO.Compression.GZipStream> pour la compression et la décompression des flux au format de données gzip.

Voir [Guide pratique pour compresser et extraire des fichiers](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Stockage isolé

Le stockage isolé est un mécanisme de stockage de données qui offre une isolation et une sécurité en définissant des méthodes standardisées pour associer du code à des données enregistrées. Le stockage fournit un système de fichiers virtuel qui est isolé par utilisateur, assembly et (éventuellement) domaine. Le stockage isolé est particulièrement utile lorsque votre application n'a pas l'autorisation d'accès aux fichiers utilisateur. Enregistrez les paramètres ou les fichiers de votre application d'une façon contrôlée par la stratégie de sécurité de l'ordinateur.

Le stockage isolé n'est pas disponible pour les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Utilisez à la place les classes de données d'application de l'espace de noms <xref:Windows.Storage?displayProperty=nameWithType>. Pour plus d’informations, consultez [Données de l’application](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Les classes suivantes sont fréquemment utilisées lors d'une implémentation de stockage isolé :

- <xref:System.IO.IsolatedStorage.IsolatedStorage> fournit la classe de base pour les implémentations de stockage isolé.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fournit une zone de stockage isolé qui contient les fichiers et les répertoires.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> expose un fichier au sein d'un stockage isolé.

Voir [Stockage isolé](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Opérations d’E/S dans les applications Windows Store

[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] contient plusieurs types pour la lecture et l'écriture dans les flux. Toutefois, cet ensemble n'inclut pas tous les types d'E/S du .NET Framework.

Quelques différences importantes sont notables pour les opérations d'E/S dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] :

- Les types spécifiquement liés aux opérations sur les fichiers, tels que <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> et <xref:System.IO.DirectoryInfo> ne sont pas inclus dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Au lieu de cela, utilisez les types dans les <xref:Windows.Storage?displayProperty=nameWithType> espace de noms du Runtime Windows, tel que <xref:Windows.Storage.StorageFile> et <xref:Windows.Storage.StorageFolder>.

- Le stockage isolé n'est pas disponible ; à la place, utilisez les [données d'application](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Utilisez les méthodes asynchrones, telles que <xref:System.IO.Stream.ReadAsync%2A> et <xref:System.IO.Stream.WriteAsync%2A> pour empêcher le blocage du thread d'interface utilisateur.

- Les types de compression <xref:System.IO.Compression.ZipFile> et <xref:System.IO.Compression.ZipFileExtensions> basés sur le chemin d’accès ne sont pas disponibles. À la place, utilisez les types dans l’espace de noms <xref:Windows.Storage.Compression?displayProperty=nameWithType>.

Vous pouvez convertir entre les flux .NET Framework et les flux Windows Runtime, si nécessaire. Pour plus d'informations, voir [Procédure : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime](how-to-convert-between-dotnet-streams-and-winrt-streams.md) ou <xref:System.IO.WindowsRuntimeStreamExtensions>.

Pour plus d’informations sur les opérations d’E/S dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], consultez [Démarrage rapide : lecture et écriture de fichiers](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>E/S et sécurité

Lorsque vous utilisez les classes de l’espace de noms <xref:System.IO?displayProperty=nameWithType>, vous devez suivre les exigences de sécurité du système d’exploitation telles que les listes de contrôle d’accès (ACL) pour contrôler l’accès aux fichiers et aux répertoires. Ces spécifications s'ajoutent aux spécifications <xref:System.Security.Permissions.FileIOPermission> existantes. Les listes de contrôle d'accès peuvent être gérées par programmation. Pour plus d'informations, voir [Procédure : ajouter ou supprimer des entrées dans la liste de contrôle d’accès](how-to-add-or-remove-access-control-list-entries.md).

Les stratégies de sécurité par défaut empêchent les applications provenant d'Internet ou de l'intranet d'accéder aux fichiers sur l'ordinateur de l'utilisateur. Par conséquent, n’utilisez pas les classes d’E/S qui requièrent un chemin d’accès à un fichier physique lors de l’écriture du code qui sera téléchargé sur Internet ou sur l’intranet. À la place, utilisez le [stockage isolé](isolated-storage.md) pour les applications .NET Framework traditionnelles ou les [données d'application](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) pour les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].

La vérification de sécurité n'est exécutée qu'à la création du flux. Par conséquent, n'ouvrez pas de flux pour le passer ensuite à du code ou à des domaines d'application d'un niveau de sécurité inférieur.

## <a name="related-topics"></a>Rubriques connexes

- [Tâches d’E/S courantes](common-i-o-tasks.md)\
Présente les tâches d’E/S associées aux fichiers, aux répertoires et aux flux, et des liens vers du contenu et des exemples appropriés pour chaque tâche.

- [E/S sur fichier asynchrones](asynchronous-file-i-o.md)\
Décrit les opérations élémentaires des E/S asynchrones et leurs avantages en termes de performances.

- [Stockage isolé](isolated-storage.md)\
Décrit un dispositif de stockage des données qui assure l'isolation et la sécurité en définissant des solutions standardisées visant à associer le code aux données enregistrées.

- [Canaux](pipe-operations.md)\
Décrit des opérations de canal nommé et anonyme dans le .NET Framework.

- [Fichiers mappés en mémoire](memory-mapped-files.md)\
Décrit les fichiers mappés en mémoire, qui contiennent le contenu de fichiers stockés sur le disque dans la mémoire virtuelle. Vous pouvez utiliser des fichiers mappés en mémoire afin de modifier des fichiers très volumineux et de créer la mémoire partagée pour la communication entre processus.
