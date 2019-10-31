---
title: Assemblys multifichiers
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 8ffb0482ebd01a056d9ffd80a74ec0332e1b8dff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119796"
---
# <a name="multifile-assemblies"></a>Assemblys multifichiers

Vous pouvez créer des assemblys multifichiers ciblant le .NET Framework à l’aide de compilateurs de ligne de commande C++ou de Visual Studio avec Visual. L’un des fichiers de l’assembly doit contenir le manifeste d’assembly. Un assembly qui démarre une application doit également contenir un point d’entrée, tel qu’une `Main` ou `WinMain` méthode.

Par exemple, supposons que vous avez une application qui contient deux modules de code, *client.cs* et *Stringer.cs*. *Stringer.cs* crée l’espace de noms `myStringer` qui est référencé par le code dans *client.cs*. *Client.cs* contient la méthode `Main`, qui est le point d’entrée de l’application. Dans cet exemple, vous compilez les deux modules de code, puis créez un troisième fichier qui contient le manifeste d’assembly, qui lance l’application. Le manifeste de l’assembly fait référence aux modules *client* et *Stringer* .

> [!NOTE]
> Les assemblys multifichiers ne peuvent avoir qu’un seul point d’entrée, même si l’assembly a plusieurs modules de code.

Il est possible de créer un assembly multifichier pour plusieurs raisons :

- Pour combiner des modules écrits dans différents langages. Il s’agit de la raison la plus courante de créer un assembly multifichier.

- Pour optimiser le téléchargement d’une application en plaçant des types rarement utilisés dans un module qui n’est téléchargé que si nécessaire.

    > [!NOTE]
    > Si vous créez des applications destinées à être téléchargées à l’aide de la balise `<object>` avec Microsoft Internet Explorer, il est important de créer des assemblys multifichiers. Dans ce scénario, vous créez un fichier distinct de vos modules de code, qui contient uniquement le manifeste d’assembly. Internet Explorer télécharge d’abord le manifeste d’assembly, puis crée des threads de travail pour télécharger tout assembly ou module supplémentaire requis. Pendant le téléchargement du fichier contenant le manifeste d’assembly, Internet Explorer ne répond pas aux entrées d’utilisateur. La durée de non-réponse d’Internet Explorer est proportionnelle à la taille du fichier contenant le manifeste d’assembly.

- Pour combiner des modules de code écrits par plusieurs développeurs. Même si chaque développeur peut compiler chaque module de code dans un assembly, ceci peut forcer l’exposition publique de certains types qui ne sont pas exposés si tous les modules sont placés dans un assembly multifichier.

Une fois que vous avez créé l’assembly, vous pouvez signer le fichier qui contient le manifeste de l’assembly, par conséquent l’assembly, ou vous pouvez attribuer un nom fort au fichier et à l’assembly et le placer dans le Global Assembly Cache.

## <a name="see-also"></a>Voir aussi

- [Comment : générer un assembly multifichier](build-multifile-assembly.md)
- [Programmer avec des assemblys](../../standard/assembly/program.md)
