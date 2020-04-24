---
title: 'Comment : appeler le compilateur de ligne de commande'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344257"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Comment : appeler le compilateur de ligne de commande (Visual Basic)

Vous pouvez appeler le compilateur de ligne de commande en tapant le nom de son fichier exécutable dans la ligne de commande, également appelée invite MS-DOS. Si vous compilez à partir de l’invite de commandes Windows par défaut, vous devez taper le chemin d’accès complet au fichier exécutable. Pour remplacer ce comportement par défaut, vous pouvez utiliser l’Invite de commandes développeur pour Visual Studio ou modifier la variable d’environnement PATH. Tous deux vous permettent de compiler à partir de n’importe quel répertoire en tapant simplement le nom du compilateur.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Pour appeler le compilateur à l’aide de l’Invite de commandes développeur pour Visual Studio

1. Ouvrez le dossier Program Visual Studio Tools dans le groupe de programmes Microsoft Visual Studio.

2. Vous pouvez utiliser le Invite de commandes développeur pour Visual Studio pour accéder au compilateur à partir de n’importe quel répertoire sur votre ordinateur, si Visual Studio est installé.

3. Appelez le Invite de commandes développeur pour Visual Studio.

4. Sur la ligne de commande, `vbc.exe` tapez *sourceFileName* , puis appuyez sur entrée.

    Par exemple, si vous avez stocké votre code source dans un `SourceFiles`répertoire appelé, vous ouvrez l’invite de commandes `cd SourceFiles` et tapez pour changer ce répertoire. Si le répertoire contient un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Pour définir la variable d’environnement PATH sur le compilateur de l’invite de commandes Windows

1. Utilisez la fonctionnalité de recherche Windows pour rechercher vbc. exe sur votre disque local.

    Le nom exact du répertoire dans lequel se trouve le compilateur dépend de l’emplacement du répertoire Windows et de la version de « .NET Framework » installée. Si vous avez plus d’une version de « .NET Framework » installée, vous devez déterminer la version à utiliser (généralement la dernière version).

2. Dans le menu **Démarrer** , cliquez avec le bouton droit sur **poste de travail**, puis cliquez sur **Propriétés** dans le menu contextuel.

3. Cliquez sous l'onglet **Avancé**, puis sur **Variables d'environnement**.

4. Dans le volet variables **système** , sélectionnez **path** dans la liste, puis cliquez sur **modifier**.

5. Dans la boîte de dialogue Modifier la variable **système** , déplacez le point d’insertion à la fin de la chaîne dans le champ valeur de la **variable** et tapez un point-virgule (;) suivi du nom de répertoire complet trouvé à l’étape 1.

6. Cliquez sur **OK** pour confirmer vos modifications et fermer les boîtes de dialogue.

     Après avoir modifié la variable d’environnement PATH, vous pouvez exécuter le compilateur Visual Basic à partir de l’invite de commandes Windows à partir de n’importe quel répertoire sur l’ordinateur.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Pour appeler le compilateur à l’aide de l’invite de commandes Windows

1. Dans le menu **Démarrer** , cliquez sur le dossier **accessoires** , puis ouvrez l' **invite de commandes Windows**.

2. Sur la ligne de commande, `vbc.exe`tapez *sourceFileName* , puis appuyez sur entrée.

     Par exemple, si vous avez stocké votre code source dans un `SourceFiles`répertoire appelé, vous ouvrez l’invite de commandes `cd SourceFiles` et tapez pour changer ce répertoire. Si le répertoire contient un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
