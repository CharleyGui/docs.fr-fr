---
title: Génération à partir de la ligne de commande avec csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789872"
---
# <a name="command-line-build-with-cscexe"></a>Génération à partir de la ligne de commande avec csc.exe

Vous pouvez invoquer le compilateur C en tapant le nom de son fichier exécutable *(csc.exe*) à une invite de commande.

Si vous utilisez la fenêtre **Invite de commandes développeur pour Visual Studio**, toutes les variables d’environnement nécessaires sont définies automatiquement. Pour plus d’informations sur la façon d’accéder à cet outil, consultez la rubrique [Invite de commandes développeur pour Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

Si vous utilisez une fenêtre Commande rapide standard, vous devez ajuster votre chemin avant de pouvoir invoquer *csc.exe* à partir de n’importe quelle sous-direction sur votre ordinateur. Vous devez également exécuter *vsvars32.bat* pour définir les variables d’environnement appropriées pour prendre en charge les builds de ligne de commande. Pour plus d’informations sur *vsvars32.bat*, y compris des instructions pour la façon de le trouver et de l’exécuter, voir [Comment définir les variables de l’environnement pour la ligne de commandement Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Si vous utilisez un ordinateur disposant uniquement du Kit de développement logiciel (SDK) Windows, vous pouvez utiliser le compilateur C# dans l’**invite de commandes du kit SDK**, disponible à partir de l’option de menu **Microsoft .NET Framework SDK**.

Vous pouvez également utiliser MSBuild pour générer des programmes en C# par programmation. Pour plus d’informations, consultez [MSBuild](/visualstudio/msbuild/msbuild).

Le fichier *exécutable csc.exe* est généralement\\situé dans le dossier Microsoft.NET-Framework*\<Version>* sous l’annuaire *Windows.* Son emplacement peut varier en fonction de la configuration exacte de l’ordinateur utilisé. Si plusieurs versions du .NET Framework sont installées sur votre ordinateur, vous trouverez plusieurs versions de ce fichier. Pour plus d’informations sur ces installations, consultez [Guide pratique pour déterminer les versions installées du .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
> Quand vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez introduire la commande **csc** et ses options de compilation associées dans la fenêtre **Sortie**. Pour afficher ces informations, suivez les instructions figurant dans [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) pour définir le niveau de détail des données de journal sur **Normal** ou **Détaillé**. Après avoir régénéré votre projet, recherchez **csc** dans la fenêtre **Sortie** pour rechercher l’appel du compilateur C#.

 **Dans ce sujet**

- [Règles pour la syntaxe de commande-ligne](#rules-for-command-line-syntax-for-the-c-compiler)

- [Exemple de lignes de commande](#sample-command-lines-for-the-c-compiler)

- [Différences entre la sortie du compilateur C et de la C](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Règles de syntaxe de ligne de commande pour le compilateur C#

Le compilateur C# utilise les règles suivantes quand il interprète les arguments spécifiés dans la ligne de commande du système d’exploitation :

- Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.

- Le signe insertion (^) n’est pas reconnu comme caractère d’échappement ni comme délimiteur. Ce caractère est traité par l’analyseur de ligne de commande du système d’exploitation avant d’être passé au tableau `argv` du programme.

- Une chaîne placée entre guillemets doubles ("chaîne") est interprétée comme un argument unique, quels que soient les espaces blancs inclus. Une chaîne entre guillemets peut être incorporée dans un argument.

- Un guillemet double précédé d’une barre oblique inverse (\\") est interprété comme un caractère guillemet double littéral (").

- Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.

- Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau `argv` pour chaque paire de barres obliques inverses, et le guillemet double est interprété comme un délimiteur de chaîne.

- Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau `argv` pour chaque paire de barres obliques inverses, et le guillemet double est « ignoré » en raison de la barre oblique inverse restante. Cela entraîne l’ajout d’un guillemet double littéral (") dans le tableau `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Exemples de lignes de commande pour le compilateur C#

- Compile *File.cs* la production *de File.exe*:

  ```console
  csc File.cs
  ```

- Compile *File.cs* la production *de File.dll*:

  ```console
  csc -target:library File.cs
  ```

- Compile *File.cs* et crée *My.exe*:

  ```console
  csc -out:My.exe File.cs
  ```

- Compile tous les fichiers C# du répertoire actif avec les optimisations activées et définit le symbole DEBUG. La sortie est *File2.exe*:

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- Compile tous les fichiers C dans l’annuaire actuel produisant une version de débogé de *File2.dll*. Aucun logo ni aucun avertissement n’est affiché :

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- Compile tous les fichiers C dans l’annuaire actuel à *Something.xyz* (un DLL):

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Différences entre les résultats de la compilation en C# et ceux de la compilation en C++

Il n’y a pas d’objets (*.obj*) fichiers créés à la suite de l’invocation du compilateur C'; les fichiers de sortie sont créés directement. Le compilateur C# n’a donc pas besoin d’un éditeur de liens.

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Options du compilateur C# par ordre alphabétique](./listed-alphabetically.md)
- [Options du compilateur C# par catégorie](./listed-by-category.md)
- [Main() et arguments de ligne de commande](../../programming-guide/main-and-command-args/index.md)
- [Arguments de la ligne de commandement](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Comment afficher les arguments de ligne de commande](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Valeurs de retour Main()](../../programming-guide/main-and-command-args/main-return-values.md)
