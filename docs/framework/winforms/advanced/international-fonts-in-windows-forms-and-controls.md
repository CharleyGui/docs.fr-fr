---
title: Polices internationales dans les formulaires et les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743522"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Polices internationales dans les Windows Forms et les contrôles

Dans les applications internationales, la méthode recommandée pour sélectionner des polices consiste à utiliser la police de secours dans la mesure du possible. La police de secours signifie que le système détermine à quel script appartient le caractère.

## <a name="using-font-fallback"></a>Utilisation de la police de secours

Pour tirer parti de cette fonctionnalité, ne définissez pas la propriété <xref:System.Drawing.Font> pour votre formulaire ou tout autre élément. L’application utilisera automatiquement la police système par défaut, qui diffère d’une langue localisée du système d’exploitation à une autre. Lorsque l’application s’exécute, le système fournit automatiquement la police correcte pour la culture sélectionnée dans le système d’exploitation.

Il existe une exception à la règle qui consiste à ne pas définir la police, qui permet de modifier le style de police. Cela peut être important pour une application dans laquelle l’utilisateur clique sur un bouton pour faire apparaître le texte dans une zone de texte en caractères gras. Pour ce faire, vous devez écrire une fonction pour modifier le style de police de la zone de texte en gras, en fonction de la police du formulaire. Il est important d’appeler cette fonction à deux emplacements : dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du bouton et dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.FontChanged>. Si la fonction est appelée uniquement dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> et qu’une autre partie du code modifie la famille de polices de la totalité du formulaire, la zone de texte ne change pas avec le reste du formulaire.

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

Toutefois, lorsque vous localisez votre application, la police en gras peut s’afficher mal pour certaines langues. Si cela pose problème, vous souhaitez que les localisateurs aient la possibilité de basculer la police du gras en texte normal. Étant donné que les localiseurs ne sont généralement pas des développeurs et n’ont pas accès au code source, seuls les fichiers de ressources, cette option doit être définie dans les fichiers de ressources. Pour ce faire, vous devez affecter à la propriété <xref:System.Drawing.Font.Bold%2A> la valeur `true`. Cela entraîne l’écriture du paramètre de police dans les fichiers de ressources, où les localiseurs peuvent le modifier. Vous écrivez ensuite le code après la méthode `InitializeComponent` pour réinitialiser la police en fonction de la police du formulaire, mais en utilisant le style de police spécifié dans le fichier de ressources.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de polices et de texte](using-fonts-and-text.md)
