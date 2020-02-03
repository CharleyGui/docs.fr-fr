---
title: Contrôles par fonction
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: f2341d49513b418c244ee7ab93c0858899502487
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741577"
---
# <a name="windows-forms-controls-by-function"></a>Classement par fonction des contrôles Windows Forms
Windows Forms propose des contrôles et des composants qui exécutent un certain nombre de fonctions. Le tableau suivant répertorie les contrôles et les composants Windows Forms selon la fonction générale. En outre, lorsque plusieurs contrôles qui remplissent la même fonction sont présents, le contrôle recommandé est listé avec une remarque concernant le contrôle qu’il a remplacé. Dans une autre table suivante, les contrôles remplacés sont répertoriés avec les remplacements recommandés.  
  
> [!NOTE]
> Les tableaux suivants ne répertorient pas tous les contrôles ou composants que vous pouvez utiliser dans Windows Forms ; pour obtenir une liste plus complète, consultez [contrôles à utiliser sur Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Contrôles et composants recommandés par fonction  
  
|Fonction|Contrôle|Description|  
|--------------|-------------|-----------------|  
|Affichage des données|Contrôle <xref:System.Windows.Forms.DataGridView>|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit une table personnalisable pour l’affichage des données. La classe <xref:System.Windows.Forms.DataGridView> permet la personnalisation des cellules, des lignes, des colonnes et des bordures. **Remarque :**  Le contrôle <xref:System.Windows.Forms.DataGridView> fournit de nombreuses fonctionnalités de base et avancées qui manquent dans le contrôle <xref:System.Windows.Forms.DataGrid>. Pour plus d’informations, consultez [différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Liaison de données et navigation|Composant <xref:System.Windows.Forms.BindingSource>|Simplifie la liaison de contrôles sur un formulaire aux données en fournissant une gestion des devises, une notification des modifications et d’autres services.|  
||Contrôle <xref:System.Windows.Forms.BindingNavigator>|Fournit une interface de type barre d’outils pour naviguer et manipuler des données dans un formulaire.|  
|Modification de texte|Contrôle <xref:System.Windows.Forms.TextBox>|Affiche le texte entré au moment du design et qui peut être modifié par les utilisateurs au moment de l’exécution ou par programme.|  
||Contrôle <xref:System.Windows.Forms.RichTextBox>|Permet d’afficher du texte avec une mise en forme en texte brut ou au format RTF (Rich-Text Format).|  
||Contrôle <xref:System.Windows.Forms.MaskedTextBox>|Limite le format des entrées utilisateur|  
|Affichage des informations (lecture seule)|Contrôle <xref:System.Windows.Forms.Label>|Affiche du texte que les utilisateurs ne peuvent pas directement modifier.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d’un lien de type Web et déclenche un événement lorsque l’utilisateur clique sur le texte spécial. Généralement, le texte est un lien vers une autre fenêtre ou un site Web.|  
||Contrôle <xref:System.Windows.Forms.StatusStrip>|Affiche des informations sur l’état actuel de l’application à l’aide d’une zone encadrée, généralement en bas d’un formulaire parent.|  
||Contrôle <xref:System.Windows.Forms.ProgressBar>|Affiche la progression actuelle d’une opération à l’utilisateur.|  
|Affichage de la page Web|Contrôle <xref:System.Windows.Forms.WebBrowser>|Autorise l’utilisateur à parcourir des pages web dans votre formulaire.|  
|Sélection dans une liste|Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d’éléments, chacun accompagné d’une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.ComboBox>|Affiche une liste déroulante d’éléments.|  
||Contrôle <xref:System.Windows.Forms.DomainUpDown>|Affiche la liste des éléments de texte que les utilisateurs peuvent parcourir à l’aide des boutons haut et PG.|  
||Contrôle <xref:System.Windows.Forms.ListBox>|Affiche une liste de texte et d’éléments graphiques (icônes).|  
||Contrôle <xref:System.Windows.Forms.ListView>|Affiche les éléments dans l’une des quatre vues différentes. Les vues comprennent uniquement du texte, du texte avec de petites icônes, du texte avec des grandes icônes et un mode Détails.|  
||Contrôle <xref:System.Windows.Forms.NumericUpDown>|Affiche la liste des chiffres auxquels les utilisateurs peuvent faire défiler à l’aide des boutons monter et descendre.|  
||Contrôle <xref:System.Windows.Forms.TreeView>|Affiche une collection hiérarchique d’objets node qui peuvent se composer de texte avec des cases à cocher ou des icônes facultatives.|  
|Affichage des graphiques|Contrôle <xref:System.Windows.Forms.PictureBox>|Affiche des fichiers graphiques, tels que des bitmaps et des icônes, dans un frame.|  
|Stockage graphique|Contrôle <xref:System.Windows.Forms.ImageList>|Sert de référentiel pour les images. <xref:System.Windows.Forms.ImageList> contrôles et les images qu’ils contiennent peuvent être réutilisés d’une application à l’autre.|  
|Paramètre de valeur|Contrôle <xref:System.Windows.Forms.CheckBox>|Affiche une case à cocher et une étiquette pour le texte. Généralement utilisé pour définir des options.|  
||Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d’éléments, chacun accompagné d’une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.RadioButton>|Affiche un bouton qui peut être activé ou désactivé.|  
||Contrôle <xref:System.Windows.Forms.TrackBar>|Permet aux utilisateurs de définir des valeurs sur une échelle en déplaçant un « curseur » sur une échelle.|  
|Paramètre de date|Contrôle <xref:System.Windows.Forms.DateTimePicker>|Affiche un calendrier graphique pour permettre aux utilisateurs de sélectionner une date ou une heure.|  
||Contrôle <xref:System.Windows.Forms.MonthCalendar>|Affiche un calendrier graphique pour permettre aux utilisateurs de sélectionner une plage de dates.|  
|Boîtes de dialogue|Contrôle <xref:System.Windows.Forms.ColorDialog>|Affiche la boîte de dialogue Sélecteur de couleurs qui permet aux utilisateurs de définir la couleur d’un élément d’interface.|  
||Contrôle <xref:System.Windows.Forms.FontDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de définir une police et ses attributs.|  
||Contrôle <xref:System.Windows.Forms.OpenFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de naviguer jusqu’à un fichier et de le sélectionner.|  
||Contrôle <xref:System.Windows.Forms.PrintDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de sélectionner une imprimante et de définir ses attributs.|  
||Contrôle <xref:System.Windows.Forms.PrintPreviewDialog>|Affiche une boîte de dialogue qui montre comment un composant de <xref:System.Drawing.Printing.PrintDocument> de contrôle s’affiche une fois imprimé.|  
||Contrôle <xref:System.Windows.Forms.FolderBrowserDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de parcourir, de créer et de sélectionner un dossier.|  
||Contrôle <xref:System.Windows.Forms.SaveFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs d’enregistrer un fichier.|  
|Contrôles de menu|Contrôle <xref:System.Windows.Forms.MenuStrip>|Crée des menus personnalisés. **Remarque :**  Le <xref:System.Windows.Forms.MenuStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.MainMenu>.|  
||Contrôle <xref:System.Windows.Forms.ContextMenuStrip>|Crée des menus contextuels personnalisés. **Remarque :**  Le <xref:System.Windows.Forms.ContextMenuStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.ContextMenu>.|  
|Commands|Contrôle <xref:System.Windows.Forms.Button>|Démarre, arrête ou interrompt un processus.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d’un lien de type Web et déclenche un événement lorsque l’utilisateur clique sur le texte spécial. Généralement, le texte est un lien vers une autre fenêtre ou un site Web.|  
||Contrôle <xref:System.Windows.Forms.NotifyIcon>|Affiche une icône dans la zone de notification d’état de la barre des tâches qui représente une application en cours d’exécution en arrière-plan.|  
||Contrôle <xref:System.Windows.Forms.ToolStrip>|Crée des barres d’outils qui peuvent avoir un Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer ou une apparence personnalisée, avec ou sans thèmes, et avec prise en charge de la réorganisation des éléments de dépassement de capacité et d’exécution. **Remarque :**  Le contrôle <xref:System.Windows.Forms.ToolStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.ToolBar>.|  
|Aide utilisateur|Composant <xref:System.Windows.Forms.HelpProvider>|Fournit une aide contextuelle ou en ligne pour les contrôles.|  
||Composant <xref:System.Windows.Forms.ToolTip>|Fournit une fenêtre contextuelle qui affiche une brève description de l’objectif d’un contrôle lorsque l’utilisateur place le pointeur sur le contrôle.|  
|Regroupement d’autres contrôles|Contrôle <xref:System.Windows.Forms.Panel>|Regroupe un ensemble de contrôles sur un frame sans étiquette défilant.|  
||Contrôle <xref:System.Windows.Forms.GroupBox>|Regroupe un ensemble de contrôles (tels que les cases d’option) sur un frame étiqueté et ne pouvant pas défiler.|  
||Contrôle <xref:System.Windows.Forms.TabControl>|Fournit une page à onglets permettant d’organiser et d’accéder efficacement aux objets groupés.|  
||Contrôle <xref:System.Windows.Forms.SplitContainer>|Fournit deux panneaux séparés par une barre mobile. **Remarque :**  Le contrôle <xref:System.Windows.Forms.SplitContainer> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.Splitter>.|  
||Contrôle <xref:System.Windows.Forms.TableLayoutPanel>|Représente un panneau qui dispose dynamiquement son contenu dans une grille composée de lignes et de colonnes.|  
||Contrôle <xref:System.Windows.Forms.FlowLayoutPanel>|Représente un panneau qui dispose dynamiquement son contenu horizontalement ou verticalement.|  
|Audio|Contrôle <xref:System.Media.SoundPlayer>|Lit les fichiers audio au format. wav. Les sons peuvent être chargés ou joués de façon asynchrone.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Contrôles et composants remplacés par fonction  
  
|Fonction|Contrôle remplacé|Remplacement recommandé|  
|--------------|------------------------|-----------------------------|  
|Affichage des données|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Affichage des informations (contrôles en lecture seule)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Contrôles de menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Commands|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Présentation des formulaires|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Voir aussi

- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
