---
title: Vue d'ensemble du contrôle ProgressBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968317"
---
# <a name="progressbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ProgressBar (Windows Forms)
> [!IMPORTANT]
> Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle <xref:System.Windows.Forms.ProgressBar> Windows Forms indique la progression d’un processus en affichant un nombre approprié de rectangles disposés dans une barre horizontale. Une fois le processus terminé, la barre est remplie. Les barres de progression sont couramment utilisées pour permettre à l’utilisateur de savoir combien de temps attendre la fin d’un processus. par exemple, lors du chargement d’un fichier volumineux.  
  
> [!NOTE]
> Le <xref:System.Windows.Forms.ProgressBar> contrôle peut uniquement être orienté horizontalement sur le formulaire.  
  
## <a name="key-properties-and-methods"></a>Propriétés et méthodes de clé  
 Les propriétés de clé du <xref:System.Windows.Forms.ProgressBar> contrôle sont <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>et <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Les <xref:System.Windows.Forms.ProgressBar.Minimum%2A> propriétés <xref:System.Windows.Forms.ProgressBar.Maximum%2A> et définissent les valeurs maximale et minimale que la barre de progression peut afficher. La <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété représente la progression effectuée vers la fin de l’opération. Étant donné que la barre affichée dans le contrôle est composée de blocs, la valeur affichée <xref:System.Windows.Forms.ProgressBar> par le contrôle se rapproche <xref:System.Windows.Forms.ProgressBar.Value%2A> uniquement de la valeur actuelle de la propriété. En fonction de la taille du <xref:System.Windows.Forms.ProgressBar> contrôle, la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété détermine quand afficher le bloc suivant.  
  
 La méthode la plus courante pour mettre à jour la valeur de progression actuelle consiste à écrire <xref:System.Windows.Forms.ProgressBar.Value%2A> du code pour définir la propriété. Dans l’exemple de chargement d’un fichier volumineux, vous pouvez définir la taille maximale du fichier, en kilo-octets. Par exemple, si la <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriété a la valeur 100, la <xref:System.Windows.Forms.ProgressBar.Minimum%2A> propriété a la valeur 10 et la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> a la valeur 50, 5 rectangles sont affichés. Il s’agit de la moitié du nombre qui peut être affiché.  
  
 Toutefois, il existe d’autres façons de modifier la valeur affichée par <xref:System.Windows.Forms.ProgressBar> le contrôle, en dehors de <xref:System.Windows.Forms.ProgressBar.Value%2A> la définition directe de la propriété. La <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété peut être utilisée pour spécifier une valeur d’incrémentation <xref:System.Windows.Forms.ProgressBar.Value%2A> de la propriété. Ensuite, l’appel <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> de la méthode incrémente la valeur. Pour faire varier la valeur d’incrément, vous pouvez <xref:System.Windows.Forms.ProgressBar.Increment%2A> utiliser la méthode et spécifier une valeur avec laquelle incrémenter la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété.  
  
 Un autre contrôle qui informe graphiquement l’utilisateur sur une action en cours est le <xref:System.Windows.Forms.StatusBar> contrôle.  
  
> [!IMPORTANT]
> Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar, contrôle](progressbar-control-windows-forms.md)
