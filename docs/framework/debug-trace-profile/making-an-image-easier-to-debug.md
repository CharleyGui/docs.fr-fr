---
title: Rendre une image plus facile à déboguer dans .NET
description: Découvrez comment configurer une image exécutable pour faciliter le débogage à l’aide de commutateurs IDE et d’options de ligne de commande.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
ms.openlocfilehash: a3305dc864e7852c2336009503732a51868410d2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558509"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Rendre une image plus facile à déboguer dans .NET

Lors de la compilation de code non managé, vous pouvez configurer une image exécutable pour le débogage en définissant des commutateurs ou des options de ligne de commande de l’IDE. Par exemple, vous pouvez utiliser l’option de ligne de commande /**Zi** dans Visual C++ pour lui demander de produire des fichiers de symboles de débogage (extension de fichier .pdb). De même, l’option de ligne de commande /**Od** indique au compilateur de désactiver l’optimisation. Le code résultant s’exécute plus lentement, mais il est plus facile à déboguer, si nécessaire.

Lors de la compilation d' .NET Framework code managé, les compilateurs tels que Visual C++, Visual Basic et C# compilent leur programme source en langage MSIL (Microsoft Intermediate Language). MSIL est ensuite compilé juste-à-temps, juste avant l’exécution, dans le code machine natif. Comme avec le code non managé, vous pouvez configurer une image exécutable pour le débogage en définissant des commutateurs ou des options de ligne de commande de l’IDE. Vous pouvez également configurer la compilation juste-à-temps pour le débogage de la même façon.

Cette configuration JIT a deux aspects :

- Vous pouvez demander au compilateur JIT de générer des informations de suivi. Ceci permet au débogueur de faire correspondre une chaîne d’instructions MSIL à son équivalent en code machine, et d’effectuer le suivi des emplacements de stockage des variables locales et des arguments de fonction. À partir de la version .NET Framework 2,0, le compilateur JIT génère toujours des informations de suivi. il n’est donc pas nécessaire de le demander.

- Vous pouvez demander au compilateur JIT de ne pas optimiser le code machine résultant.

Normalement, le compilateur qui génère le code MSIL définit ces options du compilateur JIT de manière appropriée, en fonction des commutateurs IDE ou des options de ligne de commande que vous spécifiez, par exemple/**OD**.

Dans certains cas, vous pouvez changer le comportement du compilateur JIT afin que le code machine généré soit plus facile à déboguer. Par exemple, vous pouvez générer des informations de suivi JIT pour une version commerciale ou pour l’optimisation du contrôle. Vous pouvez faire cela avec un fichier d’initialisation (.ini).

Par exemple, si l’assembly que vous souhaitez déboguer est appelé *MyApp.exe*, vous pouvez créer un fichier texte nommé *MyApp.ini*, dans le même dossier que *MyApp.exe*, qui contient ces trois lignes :

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Vous pouvez définir la valeur de chaque option sur 0 ou 1. Les options absentes ont 0 comme valeur par défaut. La définition de `GenerateTrackingInfo` sur 1 et de `AllowOptimize` sur 0 est ce qui permet le débogage le plus facile.

À partir de la version .NET Framework 2,0, le compilateur JIT génère toujours des informations de suivi, quelle que soit la valeur de `GenerateTrackingInfo` ; Toutefois, la `AllowOptimize` valeur est toujours un effet. Quand vous utilisez le générateur d’images natives [Ngen.exe (Native Image Generator)](../tools/ngen-exe-native-image-generator.md) pour précompiler l’image native sans optimisation, le fichier .ini doit être présent dans le dossier cible avec `AllowOptimize=0` quand Ngen.exe s’exécute. Si vous avez précompilé un assembly sans optimisation, vous devez supprimer le code précompilé à l’aide de NGen.exe option **/Uninstall** avant de réexécuter Ngen.exe pour précompiler le code comme optimisé. Si le fichier. ini n’est pas présent dans le dossier, par défaut Ngen.exe précompile le code comme étant optimisé.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> contrôle les paramètres pour un assembly. **DebuggableAttribute** comprend deux champs qui contrôlent si le compilateur JIT doit optimiser et/ou générer des informations de suivi. À partir de la version .NET Framework 2,0, le compilateur JIT génère toujours des informations de suivi.

Pour une version commerciale, les compilateurs ne définissent pas **DebuggableAttribute**. Par défaut, le compilateur JIT génère les performances les plus élevées et le plus difficile pour déboguer le code machine. L’activation du suivi dans JIT diminue légèrement les performances, tandis que la désactivation de l’optimisation les réduit considérablement.

**DebuggableAttribute** s’applique à la totalité d’un assembly, et non pas à des modules individuels dans l’assembly. Les outils de développement doivent donc attacher des attributs personnalisés au jeton de métadonnées de l’assembly si un assembly a déjà été créé, ou à la classe appelée **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. L’outil ALink promeut ensuite ces attributs **DebuggableAttribute** de chaque module vers l’assembly dont ils font partie. En cas de conflit, l’opération ALink échoue.

> [!NOTE]
> Dans la version 1.0 du .NET Framework, le compilateur Microsoft Visual C++ ajoute **DebuggableAttribute** quand les options du compilateur **/clr** et **/Zi** sont spécifiées. Dans la version 1,1 de la .NET Framework, vous devez ajouter **DebuggableAttribute** manuellement dans votre code ou utiliser l’option de l’éditeur de liens **/ASSEMBLYDEBUG** .

## <a name="see-also"></a>Voir aussi

- [Débogage, traçage et profilage](index.md)
- [Activation du débogage JIT-attach](enabling-jit-attach-debugging.md)
- [Activation du profilage](/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
