---
title: 'Procédure : répondre aux modifications du jeu de polices dans une application Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 9fd7f99b35730cf867bfad5da24bc3f223e9a0f8
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425335"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Procédure : répondre aux modifications du jeu de polices dans une application Windows Forms
Dans les systèmes d’exploitation Windows, un utilisateur peut modifier les paramètres de police de l’échelle du système pour afficher la police par défaut supérieure ou inférieure. Modification de ces paramètres de police est essentiel pour les utilisateurs malvoyants et nécessitent un type plus grand lire le texte sur leurs écrans. Vous pouvez ajuster votre application Windows Forms de réagir à ces modifications en augmentant ou diminuant la taille du formulaire et tous ses texte chaque fois que le jeu de polices change. Si vous souhaitez que votre formulaire pour prendre en compte les modifications dans les tailles de police dynamiquement, vous pouvez ajouter le code à votre formulaire.  
  
 En règle générale, la police par défaut utilisée par les Windows Forms est la police retournée par la <xref:Microsoft.Win32> appel d’espace de noms à `GetStockObject(DEFAULT_GUI_FONT)`. La police retournée par cet appel change uniquement lorsque la résolution d’écran change. Comme indiqué dans la procédure suivante, votre code doit modifier la police par défaut à <xref:System.Drawing.SystemFonts.IconTitleFont%2A> pour répondre aux modifications de taille de police.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Pour utiliser la police de bureau et répondre aux modifications de schéma de polices  
  
1. Créez votre formulaire et ajouter les contrôles que vous souhaitez lui. Pour plus d'informations, voir [Procédure : Créer une Application de formulaires Windows à partir de la ligne de commande](how-to-create-a-windows-forms-application-from-the-command-line.md) et [contrôles à utiliser dans les Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2. Ajoutez une référence à la <xref:Microsoft.Win32> espace de noms à votre code.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Ajoutez le code suivant au constructeur de votre formulaire pour raccorder des gestionnaires d’événements requis et pour modifier la police par défaut en cours d’utilisation pour le formulaire.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. Implémenter un gestionnaire pour le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> événement qui provoque le formulaire à l’échelle automatiquement lorsque la <xref:Microsoft.Win32.UserPreferenceCategory.Window> les modifications de catégorie.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Enfin, implémentez un gestionnaire pour le <xref:System.Windows.Forms.Form.FormClosing> événement détache le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Gestionnaire d’événements.  
  
     > [!IMPORTANT]
     > Inclure ce code provoquera une fuite de mémoire votre application.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Compilez, puis exécutez le code.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Pour modifier manuellement le jeu de polices dans Windows XP  
  
1. Pendant l’exécution de votre application Windows Forms, cliquez sur le bureau Windows et choisissez **propriétés** dans le menu contextuel.  
  
2. Dans le **propriétés d’affichage** boîte de dialogue, cliquez sur le **apparence** onglet.  
  
3. À partir de la **la taille de police** liste déroulante, sélectionnez une nouvelle taille de police.  
  
     Vous remarquerez que le formulaire est maintenant réagit aux modifications d’exécution dans le jeu de polices de bureau. Quand l’utilisateur change entre **Normal**, **grandes polices**, et **très grands caractères**, le formulaire modifie la police et s’adapte correctement.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Le constructeur dans cet exemple de code contienne un appel à `InitializeComponent`, qui est défini lorsque vous créez un nouveau projet Windows Forms dans Visual Studio. Supprimer cette ligne de code si vous générez votre application sur la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Mise à l'échelle automatique dans les Windows Forms](automatic-scaling-in-windows-forms.md)
