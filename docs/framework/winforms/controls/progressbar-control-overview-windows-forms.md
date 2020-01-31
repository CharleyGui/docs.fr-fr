---
title: Vue d'ensemble du contrôle ProgressBar
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741280"
---
# <a name="progressbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ProgressBar (Windows Forms)
> [!IMPORTANT]
> Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle Windows Forms <xref:System.Windows.Forms.ProgressBar> indique la progression d’un processus en affichant un nombre approprié de rectangles disposés dans une barre horizontale. Une fois le processus terminé, la barre est remplie. Les barres de progression sont couramment utilisées pour permettre à l’utilisateur de savoir combien de temps attendre la fin d’un processus. par exemple, lors du chargement d’un fichier volumineux.  
  
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ProgressBar> peut uniquement être orienté horizontalement sur le formulaire.  
  
## <a name="key-properties-and-methods"></a>Propriétés et méthodes de clé  
 Les propriétés de clé du contrôle <xref:System.Windows.Forms.ProgressBar> sont <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>et <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Les propriétés <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> définissent les valeurs maximale et minimale que la barre de progression peut afficher. La propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> représente la progression effectuée vers la fin de l’opération. Étant donné que la barre affichée dans le contrôle est composée de blocs, la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar> se rapproche uniquement de la valeur actuelle de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>. En fonction de la taille du contrôle <xref:System.Windows.Forms.ProgressBar>, la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> détermine quand afficher le bloc suivant.  
  
 La méthode la plus courante pour mettre à jour la valeur de progression actuelle consiste à écrire du code pour définir la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>. Dans l’exemple de chargement d’un fichier volumineux, vous pouvez définir la taille maximale du fichier, en kilo-octets. Par exemple, si la propriété <xref:System.Windows.Forms.ProgressBar.Maximum%2A> est définie sur 100, la propriété <xref:System.Windows.Forms.ProgressBar.Minimum%2A> est définie sur 10 et la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> est définie sur 50, 5 rectangles sont affichés. Il s’agit de la moitié du nombre qui peut être affiché.  
  
 Toutefois, il existe d’autres façons de modifier la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar>, en dehors de la définition directe de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>. La propriété <xref:System.Windows.Forms.ProgressBar.Step%2A> peut être utilisée pour spécifier une valeur pour incrémenter la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> par. Ensuite, l’appel de la méthode <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> incrémente la valeur. Pour faire varier la valeur d’incrément, vous pouvez utiliser la méthode <xref:System.Windows.Forms.ProgressBar.Increment%2A> et spécifier une valeur avec laquelle incrémenter la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  
  
 Un autre contrôle qui informe graphiquement l’utilisateur sur une action en cours est le contrôle <xref:System.Windows.Forms.StatusBar>.  
  
> [!IMPORTANT]
> Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> ; Toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et l’utilisation future, si vous le souhaitez.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar, contrôle](progressbar-control-windows-forms.md)
