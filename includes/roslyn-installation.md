---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526744"
---
## <a name="installation-instructions---visual-studio-installer"></a>Instructions d’installation - Visual Studio Installer

Vous pouvez rechercher **SDK .NET Compiler Platform** dans **Visual Studio Installer** de deux façons :

### <a name="install-using-the-visual-studio-installer---workloads-view"></a>Vue Installation avec Visual Studio Installer - Charges de travail

SDK .NET Compiler Platform n’est pas sélectionné automatiquement dans le cadre de la charge de travail Développement d’extensions Visual Studio. Vous devez le sélectionner comme composant facultatif.

1. Exécutez **Visual Studio Installer**.
1. Sélectionnez **Modifier**
1. Choisissez la charge de travail **Développement d’extensions Visual Studio**.
1. Ouvrez le nœud **Développement d’extensions Visual Studio** dans l’arborescence résumée.
1. Cochez la case pour **SDK .NET Compiler Platform**. Il se trouve en dernier sous les composants facultatifs.

Si vous le souhaitez, vous pouvez ajouter **l’éditeur DGML** pour afficher des graphes dans le visualiseur :

1. Ouvrez le nœud **Composants individuels** dans l’arborescence résumée.
1. Cochez la case pour **l’éditeur DGML**

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a>Onglet Installation avec Visual Studio Installer - Composants individuels

1. Exécutez **Visual Studio Installer**.
1. Sélectionnez **Modifier**
1. Sélectionnez l’onglet **Composants individuels**
1. Cochez la case pour **SDK .NET Compiler Platform**. Il se trouve en haut de la liste, sous la section **Compilateurs, outils de génération et runtimes**.

Si vous le souhaitez, vous pouvez ajouter **l’éditeur DGML** pour afficher des graphes dans le visualiseur :

1. Cochez la case pour **Éditeur DGML**. Il se trouve sous la section **Outils de code**.
