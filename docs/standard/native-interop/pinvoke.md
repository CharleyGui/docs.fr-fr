---
title: Appel de code non managé (P/Invoke)
description: Découvrez comment appeler des fonctions natives via P/Invoke dans .NET.
ms.date: 01/18/2019
ms.openlocfilehash: cde52d9d0a4e3b84fec632b615b635e7b7df3924
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678261"
---
# <a name="platform-invoke-pinvoke"></a>Appel de code non managé (P/Invoke)

P/Invoke est une technologie qui vous permet d’accéder aux structures, aux rappels et aux fonctions des bibliothèques non managées à partir de votre code managé. Une grande partie de l’API P/Invoke est contenue dans deux espaces de noms : `System` et `System.Runtime.InteropServices`. Utiliser ces deux espaces de noms vous donne les outils pour décrire la façon dont vous voulez communiquer avec le composant natif.

Commençons par l’exemple le plus courant, c’est-à-dire appeler des fonctions non managées dans votre code managé. Nous allons afficher une zone de message à partir d’une application de ligne de commande :

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

L’exemple précédent est simple, mais il ne montre pas ce dont vous avez besoin pour appeler des fonctions non managées à partir de code managé. Examinons l’exemple :

- Line #2 affiche l’instruction using pour l' `System.Runtime.InteropServices` espace de noms qui contient tous les éléments nécessaires.
- Line #8 introduit l' `DllImport` attribut. Cet attribut est crucial, car il indique au runtime qu’il doit charger la DLL non managée. La chaîne passée est la DLL où se trouve notre fonction cible. En outre, il définit le [jeu de caractères](./charset.md) à utiliser pour marshaler les chaînes. Il spécifie enfin que cette fonction appelle [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) et que le runtime doit capturer ce code d’erreur pour que l’utilisateur puisse le récupérer avec <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.
- Line #9 est le essentiel du travail P/Invoke. Elle définit une méthode managée qui a **exactement la même signature** que la méthode non managée. Notez que la déclaration a un nouveau mot clé, `extern`, qui indique au runtime qu’il s’agit d’une méthode externe et que, quand vous l’appelez, le runtime doit la trouver dans la DLL spécifiée dans l’attribut `DllImport`.

Le reste de l’exemple appelle simplement la méthode comme toute autre méthode managée.

L’exemple est similaire pour Mac OS. Le nom de la bibliothèque dans l’attribut `DllImport` doit être modifié, car Mac OS a un schéma de nommage des bibliothèques dynamiques différent. L’exemple suivant utilise la fonction `getpid(2)` pour obtenir l’ID de processus de l’application et l’afficher dans la console :

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

Le processus est semblable sur Linux. Le nom de fonction est le même, car `getpid(2)` est un appel système [POSIX](https://en.wikipedia.org/wiki/POSIX) standard.

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a>Appel de code managé à partir de code non managé

Le runtime permet une communication fluide dans les deux directions, ce qui vous donne la possibilité d’effectuer des rappels dans du code managés à partir de fonctions natives, à l’aide de pointeurs de fonction. Ce qui ressemble le plus à un pointeur de fonction dans le code managé est un **délégué**, c’est donc ce qui est utilisé pour autoriser les rappels du code natif dans le code managé.

La façon d’utiliser cette fonctionnalité est similaire au processus code managé vers du code natif préalablement décrit. Pour un rappel donné, vous définissez un délégué qui correspond à la signature et vous le passez dans la méthode externe. Le runtime s’occupe du reste.

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

Avant de parcourir l’exemple, passons en revue les signatures des fonctions non managées dont vous avez besoin. La fonction à appeler pour énumérer toutes les fenêtres a la signature suivante : `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

Le premier paramètre est un rappel. Ce rappel a la signature suivante : `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Examinons maintenant l’exemple en détail :

- la ligne 9 dans l’exemple définit un délégué qui correspond à la signature du rappel dans le code non managé. Notez la façon dont les types LPARAM et HWND sont représentés à l’aide de `IntPtr` dans le code managé.
- Les lignes 13 et 14 introduisent la fonction `EnumWindows` de la bibliothèque user32.dll.
- Les lignes 17 à 20 implémentent le délégué. Dans cet exemple simple, nous voulons simplement générer le handle dans la console.
- Enfin, dans la ligne 24, la méthode externe est appelée et transmise au délégué.

Les exemples de Linux et Mac OS sont présentés ci-dessous. Dans ces exemples, nous utilisons la fonction `ftw` qui se trouve dans `libc`, la bibliothèque C. Cette fonction est utilisée pour parcourir des hiérarchies de répertoires et accepte un pointeur vers une fonction comme l’un de ses paramètres. Cette fonction a la signature suivante : `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

Un exemple Mac OS utilise la même fonction et la seule différence réside dans l’argument de l’attribut `DllImport`, car Mac OS conserve `libc` dans un emplacement différent.

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

Les deux exemples précédents dépendent de paramètres et dans les deux cas, les paramètres sont fournis comme des types managés. Le runtime prend « la bonne décision » et les traite dans leurs équivalents de l’autre côté. Découvrez comment les types sont marshalés en code natif sur notre page consacrée au [Marshaling de types](type-marshaling.md).

## <a name="more-resources"></a>Plus de ressources

- [Wiki PInvoke.net](https://www.pinvoke.net/), un excellent Wiki avec des informations sur les API Windows courantes et comment les appeler.
- [P/Invoke dans C++/CLI](/cpp/dotnet/native-and-dotnet-interoperability)
- [Documentation Mono sur P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
