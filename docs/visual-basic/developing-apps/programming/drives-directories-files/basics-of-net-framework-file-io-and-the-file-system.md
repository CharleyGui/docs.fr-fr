---
title: Concepts de base du système de fichiers et des E/S de fichier du .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 5d60d0089d042c0be343c741c26de0b4b7778d6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348942"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Concepts de base du système de fichiers et des E/S de fichier du .NET Framework (Visual Basic)

Les classes de l’espace de noms <xref:System.IO> sont utilisées pour travailler avec les lecteurs, les fichiers et les répertoires.

L’espace de noms <xref:System.IO> contient les classes <xref:System.IO.File> et <xref:System.IO.Directory>, qui fournissent la fonctionnalité .NET Framework permettant de manipuler des fichiers et des répertoires. Les méthodes de ces objets étant des membres statiques ou partagés, vous pouvez les utiliser directement sans créer d’abord une instance de la classe. Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo>, familières aux utilisateurs de la fonctionnalité `My`, sont associées à ces classes. Pour utiliser ces classes, vous devez qualifier complètement les noms ou importer les espaces de noms appropriés en incluant les instructions `Imports` au début du code affecté. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Les autres rubriques de cette section utilisent l’objet `My.Computer.FileSystem` au lieu des classes `System.IO` pour travailler avec des lecteurs, des fichiers et des répertoires. L’objet `My.Computer.FileSystem` est destiné principalement à une utilisation dans des programmes Visual Basic. Les classes `System.IO` sont destinées à être utilisées par tout langage qui prend en charge le .NET Framework, notamment Visual Basic.

## <a name="definition-of-a-stream"></a>Définition d’un flux

Le .NET Framework utilise des flux pour prendre en charge la lecture et l’écriture dans des fichiers. Vous pouvez considérer un flux comme un ensemble unidimensionnel de données contiguës, ayant un début et une fin, et où le curseur indique la position actuelle dans le flux.

![Le curseur montre la position actuelle dans FileStream.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Opérations de flux

Les données contenues dans le flux peuvent provenir de la mémoire, d’un fichier ou d’un socket TCP/IP. Des opérations fondamentales peuvent être appliquées aux flux :

- **Lecture**. Vous pouvez lire à partir d’un flux, autrement dit transférer des données du flux vers une structure de données, telle qu’une chaîne ou un tableau d’octets.

- **Écriture**. Vous pouvez écrire dans un flux, autrement dit transférer des données d’une source de données vers le flux.

- **Recherche**. Vous pouvez interroger et modifier votre position dans le flux.

Pour plus d'informations, consultez [Composing Streams](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Types de flux

Dans le .NET Framework, un flux est représenté par la classe <xref:System.IO.Stream>, qui forme la classe abstraite pour tous les autres flux. Vous ne pouvez pas créer directement une instance de la classe <xref:System.IO.Stream>. Vous devez utiliser l’une des classes qu’elle implémente.

Il existe de nombreux types de flux, mais dans le cadre de l’utilisation des entrées/sorties (E/S) de fichiers, les types les plus importants sont la classe <xref:System.IO.FileStream>, qui permet de lire et d’écrire dans des fichiers, et la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>, qui permet de créer des fichiers et des répertoires dans un stockage isolé. Voici d’autres flux qui peuvent être utilisés avec les E/S de fichiers :

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

Le tableau suivant répertorie les tâches couramment accomplies avec un flux :

|À|Consultez|
|---|---|
|Lire et écrire dans un fichier de données|[Comment : lire et écrire dans un fichier de données créé récemment](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Lire le texte d’un fichier|[Comment : lire du texte dans un fichier](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Écrire du texte dans un fichier|[Comment : écrire du texte dans un fichier](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Lire les caractères d’une chaîne|[Comment : lire les caractères d'une chaîne](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Écrire des caractères dans une chaîne|[Comment : écrire des caractères dans une chaîne](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Chiffrer les données|[Chiffrement de données](../../../../standard/security/encrypting-data.md)|
|Déchiffrer des données|[Déchiffrement de données](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Accès aux fichiers et attributs

Vous pouvez contrôler la façon dont les fichiers sont créés, ouverts et partagés avec les énumérations <xref:System.IO.FileAccess>, <xref:System.IO.FileMode> et <xref:System.IO.FileShare>, qui contiennent les indicateurs utilisés par les constructeurs de la classe <xref:System.IO.FileStream>. Par exemple, quand vous ouvrez ou créez un <xref:System.IO.FileStream>, l’énumération <xref:System.IO.FileMode> vous permet de spécifier si le fichier est ouvert pour l’ajout, si un fichier est créé si le fichier spécifié n’existe pas, si le fichier est remplacé, et ainsi de suite.

L’énumération <xref:System.IO.FileAttributes> vous permet de recueillir des informations propres au fichier. L’énumération <xref:System.IO.FileAttributes> retourne les attributs stockés du fichier, par exemple s’il est compressé, chiffré, caché, en lecture seule, s’il s’agit d’une archive, d’un répertoire, d’un fichier système ou d’un fichier temporaire.

Le tableau suivant répertorie les tâches qui impliquent l’accès aux fichiers et les attributs de fichiers :

|À|Consultez|
|---|---|
|Ouvrir un fichier journal et y ajouter du texte|[Comment : ouvrir un fichier journal et y ajouter des éléments](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Déterminer les attributs d’un fichier|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Autorisations de fichiers

Vous pouvez contrôler l’accès aux fichiers et aux répertoires avec la classe <xref:System.Security.Permissions.FileIOPermission>. Cela peut être particulièrement important pour les développeurs qui travaillent avec des Web Forms, qui s’exécutent par défaut dans le contexte d’un compte d’utilisateur local spécial nommé ASPNET, créé dans le cadre des installations d’ASP.NET et .NET Framework. Quand une telle application demande l’accès à une ressource, le compte d’utilisateur ASPNET dispose d’autorisations limitées, ce qui peut empêcher l’utilisateur d’effectuer des actions telles que l’écriture dans un fichier à partir d’une application web. Pour plus d’informations, consultez <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Stockage de fichiers isolé

Le stockage isolé est une tentative de résolution des problèmes créés lors de l’utilisation de fichiers, quand l’utilisateur ou le code n’a pas les autorisations nécessaires. Le stockage isolé assigne à chaque utilisateur un compartiment de données qui peut contenir un ou plusieurs magasins. Les magasins peuvent être isolés les uns des autres par utilisateur et par assembly. Seul l’utilisateur et l’assembly ayant créé un magasin y ont accès. Un magasin se comporte comme un système de fichiers virtuel complet : vous pouvez y créer et y manipuler des fichiers et des répertoires.

Le tableau suivant répertorie les tâches couramment associées au stockage de fichiers isolé.

|À|Consultez|
|---|---|
|Créer un magasin isolé|[Obtention de magasins](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Énumérer les magasins isolés|[Énumération de magasins](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Supprimer un magasin isolé|[Suppression de magasins](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Créer un fichier ou un répertoire dans un stockage isolé|[Comment : créer des fichiers et des répertoires dans un stockage isolé](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Rechercher un fichier dans un stockage isolé|[Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Lire ou écrire dans un fichier dans un stockage isolé|[Lecture et écriture dans des fichiers](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Supprimer un fichier ou un répertoire dans un stockage isolé|[Comment : supprimer des fichiers et des répertoires dans un stockage isolé](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Événements de fichiers

Le composant <xref:System.IO.FileSystemWatcher> vous permet de surveiller les modifications dans les fichiers et répertoires de votre système ou sur n’importe quel ordinateur auquel vous avez accès par le biais du réseau. Par exemple, si un fichier est modifié, vous souhaiterez peut-être envoyer à un utilisateur une alerte signalant la modification. Quand des modifications se produisent, un ou plusieurs événements sont déclenchés, stockés dans une mémoire tampon et transmis au composant <xref:System.IO.FileSystemWatcher> pour traitement.

## <a name="see-also"></a>Voir aussi

- [Composing Streams](../../../../standard/io/composing-streams.md)
- [Fichier et stream I/O](../../../../standard/io/index.md)
- [E/S sur fichier asynchrones](../../../../standard/io/asynchronous-file-i-o.md)
- [Classes utilisées dans les E/S de fichier du .NET Framework et le système de fichiers (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
