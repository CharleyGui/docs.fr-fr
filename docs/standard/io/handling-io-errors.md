---
title: Gestion des erreurs E/S dans .NET
description: Découvrez comment gérer les erreurs d’e/s dans .NET. Mappez les codes d’erreur aux exceptions, gérez les exceptions dans les opérations d’e/s et gérez IOException.
ms.date: 08/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bd7112b3052f246a01e4a36d6d425b37cb6174dd
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188040"
---
# <a name="handling-io-errors-in-net"></a>Gestion des erreurs E/S dans .NET

Outre les exceptions qui peuvent être levées dans n’importe quel appel de méthode (comme <xref:System.OutOfMemoryException> lorsqu’un système est sous contrainte ou <xref:System.NullReferenceException> en raison d’erreurs de programmation), les méthodes du système de fichiers .NET peuvent lever les exceptions suivantes :

- <xref:System.IO.IOException?displayProperty=nameWithType>, la classe de base de tous les types d’exceptions <xref:System.IO>. Elle est levée pour les erreurs dont les codes d’erreur à partir du système d’exploitation ne sont pas directement mappés vers un autre type d’exception.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, qui est levée pour les caractères de chemin non valides sur le .NET Framework et .NET Core 2.0 et les versions précédentes.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, qui est levée pour les deux-points non valides dans le .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, qui est levée pour les applications exécutées en mode de confiance limitée et qui ne disposent pas des autorisations nécessaires sur le .NET Framework uniquement. (La confiance totale est la valeur par défaut sur le .NET Framework.)

## <a name="mapping-error-codes-to-exceptions"></a>Mappage des codes d'erreur aux exceptions

Étant donné que le système de fichiers est une ressource de système d’exploitation, les méthodes E/S dans .NET Core et .NET Framework encapsulent les appels avec le système d’exploitation sous-jacent. Lorsqu’une erreur E/S se produit dans le code exécuté par le système d’exploitation, celui-ci retourne des informations sur l’erreur à la méthode E/S .NET. La méthode convertit ensuite les informations sur l’erreur, généralement sous la forme d’un code d’erreur, dans un type d’exception .NET. Dans la plupart des cas, cela signifie traduire directement le code d’erreur dans son type d’exception correspondant. La méthode n’effectue pas un mappage spécial de l’erreur en fonction du contexte de l’appel de la méthode.

Par exemple, sur le système d’exploitation Windows, un appel de méthode qui retourne un code d’erreur `ERROR_FILE_NOT_FOUND` (ou 0x02) est mappé à <xref:System.IO.FileNotFoundException> et le code d’erreur `ERROR_PATH_NOT_FOUND` (ou 0x03) correspond à <xref:System.IO.DirectoryNotFoundException>.

Toutefois, les conditions précises sous lesquelles le système d’exploitation retourne des codes d’erreur particuliers sont souvent non documentées ou mal documentées. Par conséquent, des exceptions inattendues peuvent se produire. Par exemple, étant donné que vous travaillez avec un répertoire au lieu d’un fichier, vous pourriez penser que le fait de fournir un chemin d’accès de répertoire non valide au constructeur <xref:System.IO.DirectoryInfo.%23ctor%2A> lèverait une exception <xref:System.IO.DirectoryNotFoundException>. Toutefois, une exception <xref:System.IO.FileNotFoundException> peut également être levée.

## <a name="exception-handling-in-io-operations"></a>Gestion des exceptions dans les opérations E/S

En raison de cette dépendance envers le système d’exploitation, des conditions d’exception identiques (par exemple, l’erreur répertoire introuvable dans ce cas) peuvent faire qu’une méthode E/S lève l’une des exceptions de la classe entière d’exceptions E/S. Cela signifie que, lors de l’appel d’API E/S, votre code doit être prêt à gérer la plupart ou toutes ces exceptions, comme indiqué dans le tableau suivant :

| Type d'exception | .NET Core/. NET 5 + | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Oui | Oui |
| <xref:System.IO.FileNotFoundException> | Oui | Oui |
| <xref:System.IO.DirectoryNotFoundException> | Oui | Oui |
| <xref:System.IO.DriveNotFoundException?> | Oui | Oui |
| <xref:System.IO.PathTooLongException> | Oui | Oui |
| <xref:System.OperationCanceledException> | Oui | Oui |
| <xref:System.UnauthorizedAccessException> | Oui | Oui |
| <xref:System.ArgumentException> | .NET Core 2.0 et versions antérieures| Oui |
| <xref:System.NotSupportedException> | Non | Oui |
| <xref:System.Security.SecurityException> | Non | Confiance limitée uniquement |

## <a name="handling-ioexception"></a>Gestion d’IOException

Comme la classe de base pour les exceptions dans l’espace de noms <xref:System.IO>, <xref:System.IO.IOException> est également levée pour n’importe quel code d’erreur qui n’est pas mappé à un type d’exception prédéfini. Cela signifie qu’elle peut être levée par n’importe quelle opération E/S.

> [!IMPORTANT]
> Étant donné que <xref:System.IO.IOException> est la classe de base des autres types d’exception dans l’espace de noms <xref:System.IO>, vous devez la gérer dans un bloc `catch` une fois que vous avez géré les autres exceptions E/S associées.

En outre, à compter de .NET Core 2.1, les contrôles de validation de l’exactitude du chemin d’accès (par exemple, pour s’assurer que des caractères non valides ne sont pas présents dans un chemin d’accès) ont été supprimés, et le runtime lève une exception mappée à partir d’un code d’erreur de système d’exploitation plutôt qu’à partir de son propre code de validation. L’exception la plus susceptible d’être levée dans ce cas est <xref:System.IO.IOException>, bien que n’importe quel autre type d’exception puisse également être levé.

Notez que, dans votre code gestion des exceptions, vous devez toujours gérer <xref:System.IO.IOException> en dernier. Sinon, étant donné qu’il s’agit de la classe de base de toutes les autres exceptions d’E/S, les blocs catch des classes dérivées ne seront pas évalués.

Dans le cas de <xref:System.IO.IOException>, vous pouvez obtenir des informations supplémentaires sur l’erreur à partir de la propriété [IOException.HResult](xref:System.Exception.HResult). Pour convertir la valeur HResult en un code d’erreur Win32, éliminez les 16 bits supérieurs de la valeur de 32 bits. Le tableau suivant répertorie les codes d’erreur qui peuvent être encapsulés dans <xref:System.IO.IOException>.

| HResult | Constante | Description |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Le nom de fichier est manquant ou le fichier ou le répertoire est en cours d’utilisation. |
| ERROR_FILE_EXISTS | 80 | Le fichier existe déjà. |
| ERROR_INVALID_PARAMETER | 87 | Un argument fourni à la méthode n’est pas valide. |
| ERROR_ALREADY_EXISTS | 183 | Le fichier ou le répertoire existe déjà. |

Vous pouvez les gérer à l’aide d’une clause `When` dans une instruction catch, comme le montre l’exemple suivant.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Voir aussi

- [Gestion et levée d’exceptions dans .NET](../exceptions/index.md)
- [Gestion des exceptions (bibliothèque parallèle de tâches)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Bonnes pratiques pour les exceptions](../exceptions/best-practices-for-exceptions.md)
- [Utiliser des exceptions spécifiques dans un bloc Catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
