---
title: Répondre aux modifications de jeu de polices dans une application Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739229"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Comment : répondre aux modifications de jeu de polices dans une application Windows Forms
Dans les systèmes d’exploitation Windows, un utilisateur peut modifier les paramètres de police à l’échelle du système pour que la police par défaut apparaisse plus grande ou plus petite. La modification de ces paramètres de police est essentielle pour les utilisateurs qui sont affectés visuellement et qui nécessitent un plus grand type de lecture du texte sur leurs écrans. Vous pouvez ajuster votre application Windows Forms pour réagir à ces modifications en accroissant ou en diminuant la taille du formulaire et de tout le texte contenu chaque fois que le jeu de polices change. Si vous souhaitez que votre formulaire accepte les modifications de taille de police de manière dynamique, vous pouvez ajouter du code à votre formulaire.  
  
 En règle générale, la police par défaut utilisée par Windows Forms est la police retournée par l’appel de l’espace de noms <xref:Microsoft.Win32> à `GetStockObject(DEFAULT_GUI_FONT)`. La police retournée par cet appel change uniquement lorsque la résolution d’écran change. Comme indiqué dans la procédure suivante, votre code doit modifier la police par défaut en <xref:System.Drawing.SystemFonts.IconTitleFont%2A> pour répondre aux modifications de la taille de police.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Pour utiliser la police du bureau et répondre aux modifications du jeu de polices  
  
1. Créez votre formulaire et ajoutez-y les contrôles qui vous intéressent. Pour plus d’informations, consultez [Comment : créer un Windows Forms application à partir de la ligne de commande](how-to-create-a-windows-forms-application-from-the-command-line.md) et des [contrôles à utiliser sur Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2. Ajoutez une référence à l’espace de noms <xref:Microsoft.Win32> dans votre code.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Ajoutez le code suivant au constructeur de votre formulaire pour raccorder les gestionnaires d’événements requis et modifier la police par défaut en cours d’utilisation pour le formulaire.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. Implémentez un gestionnaire pour l’événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> qui provoque la mise à l’échelle automatique du formulaire lorsque la catégorie <xref:Microsoft.Win32.UserPreferenceCategory.Window> change.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Enfin, implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.FormClosing> qui détache le gestionnaire d’événements <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.  
  
     > [!IMPORTANT]
     > Si vous n’incluez pas ce code, votre application risque de provoquer une fuite de mémoire.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Compilez, puis exécutez le code.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Pour modifier manuellement le jeu de polices dans Windows XP  
  
1. Pendant que votre application Windows Forms est en cours d’exécution, cliquez avec le bouton droit sur le bureau Windows, puis choisissez **Propriétés** dans le menu contextuel.  
  
2. Dans la boîte de dialogue **propriétés d’affichage** , cliquez sur l’onglet **apparence** .  
  
3. Dans la zone de liste déroulante taille de la **police** , sélectionnez une nouvelle taille de police.  
  
     Vous remarquerez que le formulaire réagit maintenant aux modifications au moment de l’exécution dans le schéma de police du bureau. Lorsque l’utilisateur change de police **normale**, de **grandes polices**et de très **grandes polices**, le formulaire change la police et s’adapte correctement.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Le constructeur de cet exemple de code contient un appel à `InitializeComponent`, qui est défini lorsque vous créez un projet de Windows Forms dans Visual Studio. Supprimez cette ligne de code si vous générez votre application sur la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Mise à l'échelle automatique dans les Windows Forms](automatic-scaling-in-windows-forms.md)
